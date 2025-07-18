# UlasimApp - Java Tabanlı Ulaşım Rota Planlama Uygulaması

<img width="1914" height="1137" alt="Image" src="https://github.com/user-attachments/assets/a1e8e641-1934-48c1-84a3-00457a597a6b" />


## ✨ Genel Tanıtım

**UlasimApp**, Java Swing ile geliştirilmiş, harita mantığı arkaplanda olan bir rota planlama uygulamasıdır. Kullanıcılar, başlangıç ve bitiş noktalarını arayüzden seçerek, en uygun rotayı **süre, ücret ve mesafe** açısından karşılaştırmalı olarak görebilir.

> Bu proje, **Kocaeli Üniversitesi Bilgisayar Mühendisliği 2. sınıf Prolab dersi** kapsamında gerçekleştirilmiştir. Öğrencilere yazılım mühendisliği ilkelerini uygulama imkânı sağlayan bu proje, aynı zamanda takım çalışması, tasarım prensipleri ve yazılım mimarisi açısından da önemli deneyimler sunmuştur.

Uygulama, **SOLID prensipleri** ışığında tasarlanmış olup geliştirilmeye ve genişletilmeye uygun mimarisi sayesinde gelecekte daha büyük sistemlere entegre edilebilir.

---

![Image](https://github.com/user-attachments/assets/2bd849e6-8650-43ac-a40b-1c4aaa87fe3f)

## 📚 Öne Çıkan Özellikler

- Harita paneli üzerinden rota noktaları belirleme (graf yapısı mantığı)
- En uygun rota analizleri: ⏱️ En kısa süreli / 💸 En ucuz / 📏 En kısa mesafe
- Ödeme tipleri: 💳 Kredi Kartı, 🪙 Nakit, 🟦 KentKart
- Kullanıcı profilleri: 👵 Yaşlı, 👨‍🏫 Öğretmen, 🧑‍🎓 Öğrenci, 👤 Genel, ♿ Engelli
- Ödeme türüne özel sesli bildirim desteği
- Haversine ve Manhattan gibi algoritmalarla mesafe stratejisi
- JSON formatında durak ve bağlantı verisi yükleme
- GUI destekli menüler: Ayarlar, Profil, Ödeme, Yardım

---

## 📁 Proje Yapısı

```plaintext
src/
 ├── main/App.java                         # Ana uygulama giriş noktası
 ├── ui/UlasimArayuzu.java                # Ana Swing kullanıcı arayüzü
 ├── ui/HaritaPanel.java                  # Harita paneli ve durak çizimi
 ├── ui/dialog/                           # Yardımcı ayar diyalogları
 │   ├── AboutDialog.java
 │   ├── FAQDialog.java
 │   ├── PaymentDialog.java
 │   ├── PreferencesDialog.java
 │   └── ProfileDialog.java
 ├── service/                              # Uygulama mantığı servisleri
 │   ├── RouteService.java
 │   ├── RouteCalculator.java
 │   ├── SoundPlayer.java
 │   ├── VeriYukleyici.java
 │   ├── HaversineHesaplayici.java
 │   ├── ManhattanHesaplayici.java
 │   └── IMesafeHesaplayici.java
 ├── model/                                # Veri modeli ve soyutlamalar
 │   ├── vehicle/                          # Araçlar
 │   │   ├── Arac.java
 │   │   ├── Otobus.java
 │   │   ├── Taksi.java
 │   │   └── Tramvay.java
 │   ├── payment/                          # Ödeme yöntemleri
 │   │   ├── PaymentMethod.java
 │   │   ├── KentKart.java
 │   │   ├── KrediKarti.java
 │   │   └── Nakit.java
 │   ├── passanger/                        # Yolcu türleri
 │   │   ├── IYolcu.java
 │   │   ├── GenelYolcu.java
 │   │   ├── Yasli.java
 │   │   ├── Engelli.java
 │   │   ├── Ogrenci.java
 │   │   └── Ogretmen.java
 │   └── routing/                          # Duraklar ve bağlantılar
 │       ├── Durak.java
 │       ├── DurakBaglanti.java
 │       └── DurakTransfer.java
```

---

## 🌐 SOLID Prensipleri

**S - Single Responsibility Principle**
> Her sınıf yalnızca bir sorumluluğa sahiptir. Örn: `SoundPlayer` yalnızca ses çalar, `VeriYukleyici` yalnızca veriyi yükler.

**O - Open/Closed Principle**
> Mevcut kodu bozmadan yeni ödeme türü veya yolcu tipi kolayca eklenebilir.

**L - Liskov Substitution Principle**
> `Yolcu`, `Öğretmen` ya da `Yaşlı` türleri birbirinin yerine sorunsuz geçebilir.

**I - Interface Segregation Principle**
> `IYolcu` ve `IMesafeHesaplayici` yalnızca ilgili işlemleri tanımlar.

**D - Dependency Inversion Principle**
> `RouteService` gibi sınıflar, `IMesafeHesaplayici` gibi soyutlamalar üzerinden çalışır.

---

![image](https://github.com/user-attachments/assets/86e4a395-344a-4b21-a09d-296fcd477103)



## 🚀 Projeyi Çalıştırma

### `.bat` Dosyasıyla (Windows)
```bat
@echo off
cd /d "%~dp0"
if not exist "bin" mkdir bin
javac -cp "lib/json-20210307.jar" -d bin src/main/*.java src/model/routing/*.java src/model/passanger/*.java  src/model/payment/*.java src/model/vehicle/*.java   src/service/*.java src/ui/*.java src/ui/dialog/*.java 
if %errorlevel% neq 0 exit /b %errorlevel%
java -cp "bin;lib/json-20210307.jar" main.App
pause
```

> Bu `.bat` dosyasını opsiyonel olarak `.exe` veya `.jar` formatına dönüştürerek çalıştırabilirsiniz.

---

<img width="811" height="102" alt="Image" src="https://github.com/user-attachments/assets/5e549bb6-2bbd-4996-a6c2-51e2fd8dbcea" />

## 👨‍💻 Geliştirici Ekibi

- Sadık Gölpek – [github.com/sadikgolpekk](https://github.com/sadikgolpekk)
- Ali Kılınç – [github.com/aliiklnc](https://github.com/aliiklnc)

> Bu proje, Java ile nesne yönelimli programlamaya dair güçlü örnekler sunar. SOLID prensiplerine göre inşa edilerek sürdürülebilir ve genişletilebilir bir yapıya kavuşmuştur.

---

## 📌 Notlar

- Harita görüntüsü kullanılmamıştır, sadece grafik olarak bağlantılar arkaplanda gösterilir.
- Proje genişletmeye uygun şekilde yazılmıştır.
- Diyaloglar (`About`, `Payment`, `Preferences`, vs.) arayüz etkileşimini artırmak için modüler yapıda düşünülmüştür.

 
---

## 📜 Lisans

 Özgürce kullanılabilir, değiştirilebilir.

> ⭐ Projeyi faydalı bulduysanız GitHub sayfamıza yıldız bırakmayı unutmayın!

