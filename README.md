# TasKagitMakas-Proje
 Taş, Kağıt ve Makas oyunu denemesi.
Bu proje, klasik "Taş, Kağıt, Makas" oyununu hem GUI (Grafiksel Kullanıcı Arayüzü) hem de terminal üzerinden oynanabilir hale getirmeyi amaçlayan bir uygulamadır. Python kullanılarak geliştirilen bu oyunda, kullanıcı ile bilgisayar arasında oynanan oyunlar, belirli bir sayıdaki tura göre sonuçlandırılır. Oyunun temel mantığı, taş, kağıt ve makas arasındaki ilişkileri belirleyerek hangi seçimin kazanacağını, kaybedeceğini veya berabere kalacağını hesaplamaktadır. Yapay zeka (YZ) özelliği, oyuncunun geçmiş hamlelerini analiz ederek ve belirli stratejiler doğrultusunda hareket ederek daha dinamik bir oyun deneyimi sunar. YZ, oyuncunun son hamlesine göre seçim yapar ve kişilikli mesajlar ile duruma uygun tepkiler verir. GUI versiyonu, Tkinter kütüphanesi kullanılarak kullanıcı dostu bir arayüz sunarken, terminal versiyonu daha temel ve metin tabanlı bir etkileşim sağlar. Her iki versiyon da oyun sonucunu, puanları ve oyunun devam edip etmeyeceğini yönetir, ve kullanıcıya yeni bir oyun oynama seçeneği sunar.

## Özellikler
Grafiksel Kullanıcı Arayüzü (GUI): Tkinter kütüphanesi kullanılarak oluşturulmuş, kullanıcı dostu bir arayüz sunar.
Terminal Modu: Metin tabanlı etkileşim sağlar, GUI'den bağımsız olarak çalışır.
Yapay Zeka: Oyuncunun geçmiş hamlelerini analiz ederek dinamik ve stratejik seçimler yapar.
Puan Sistemi: Beraberlik durumunda her iki taraf da puan alır, kazanan 1 puan, kaybeden ise 0 puan alır.
Yeni Oyun Seçeneği: Oyun sonunda yeni bir oyun başlatma veya çıkma seçeneği sunar.

# Teknik Detaylar
Python Sürümü: 3.1
Kütüphaneler: Tkinter (GUI için), random (bilgisayar seçimleri için)
### Fonksiyonlar:
tas_kagit_makas_Kagan_Agin_Aksoy(): GUI modunda oyunu başlatan ve yöneten ana fonksiyon.
terminal_versiyonu(): Terminal modunda oyunu yöneten fonksiyon.
yapay_zeka_mesaj(): Yapay zekanın duruma göre mesajlar oluşturduğu fonksiyon.
yapay_zeka_secimi(): Yapay zekanın oyuncunun hamlesine göre seçim yapmasını sağlayan fonksiyon.

# Kullanılan Döngüler

## while Döngüsü
while döngüsü, belirli bir koşul sağlandığı sürece kod bloğunu tekrar eder. Bu proje içinde iki ana kullanım alanı bulunmaktadır:

### GUI ve Terminal Arasında Geçiş:

    if __name__ == "__main__":
    baslangic_ekrani()

    
Bu döngü, Tkinter GUI penceresi açık olduğu sürece, kullanıcıdan hamleleri almak ve sonuçları göstermek için window.mainloop() fonksiyonunu çalıştırır. window.mainloop() bir döngü olarak çalışır ve GUI'nin kapanmasına kadar sürekli olarak olayları (buton tıklamaları, pencere kapama vb.) kontrol eder.

### Oyun Süreçlerinin Yönetimi:

Oyun sonuçlarının ve puanların hesaplanması, oyun bitiş koşullarının değerlendirilmesi gibi işlemler while döngüsü içinde yönetilmez. Ancak, GUI modunda oyunun döngüsü Tkinter tarafından yönetilen bir olay döngüsü olarak işlev görür.

## for Döngüsü
for döngüsü, bir koleksiyon (liste, sözlük, vb.) üzerinde iterasyon yaparak her bir eleman üzerinde işlem yapmak için kullanılır. Bu proje içinde aşağıdaki gibi kullanılmıştır:

### Yapay Zeka Mesajları:

    def yapay_zeka_mesaj(durum):
    """Oyuncu ile esprili bir şekilde sohbet eden yapay zeka."""
    if durum == 'kazanma':
        return random.choice(duygusal_mesajlar['kazanma'])
    elif durum == 'kaybetme':
        return random.choice(duygusal_mesajlar['kaybetme'])
    else:
        return random.choice(duygusal_mesajlar['beraberlik'])

 Burada, random.choice() fonksiyonu kullanılarak duygusal_mesajlar sözlüğündeki ilgili liste içinden rastgele bir mesaj seçilir. duygusal_mesajlar sözlüğü for döngüsü ile değil, doğrudan random.choice() ile işlenir.

 ### Oyuncunun Seçimini Gösterme:

     def sonuc_goster(oyuncu_secimi):
    """Bir tur sonucunu hesaplayıp ekrana gösterir."""
    global oyuncu_galibiyet, bilgisayar_galibiyet, tur, oyun_devam

    if not oyun_devam:
        return
    
    # Bilgisayarın seçimi (yapay zeka ile)
    bilgisayar_secimi = yapay_zeka_secimi()
    
    # Sonuçları belirleme
    if oyuncu_secimi == bilgisayar_secimi:
        ...
    elif (oyuncu_secimi == "taş" and bilgisayar_secimi == "makas") or \
         (oyuncu_secimi == "makas" and bilgisayar_secimi == "kağıt") or \
         (oyuncu_secimi == "kağıt" and bilgisayar_secimi == "taş"):
        ...
    else:
        ...

  Bu kodda, oyuncunun ve bilgisayarın seçimleri arasındaki ilişkiler belirlenir ve sonuçlar hesaplanır. Burada doğrudan bir for döngüsü kullanılmaz, ancak if-elif-else yapıları sonucunda belirli kararlar verilir.




   
