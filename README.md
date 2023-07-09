# Python Web Kazıma Dersleri

- [Python Web Kazıma Dersleri](#python-web-kazıma-dersleri)
- [1. Web Kazıma (Web Scraping) Nedir?](#1-web-kazıma-web-scraping-nedir)
- [2. Web Kazıma Önlemleri](#2-web-kazıma-önlemleri)
  - [2.1. Neden Önlem Alınıyor?](#21-neden-önlem-alınıyor)
  - [2.2. Hangi Önlemler Alınıyor?](#22-hangi-önlemler-alınıyor)
- [3. Bilinmesinde Yarar Olacak Teknik Bilgiler](#3-bilinmesinde-yarar-olacak-teknik-bilgiler)
  - [3.1. HTML Nedir?](#31-html-nedir)
  - [3.2. XML Nedir?](#32-xml-nedir)
  - [3.3. HTTP Nedir? HTTP İstekleri Nelerdir?](#33-http-nedir-http-i̇stekleri-nelerdir)
  - [3.4. Web Kazımada Karşılaşılabilecek HTTP Durum Kodları](#34-web-kazımada-karşılaşılabilecek-http-durum-kodları)
- [4. Kullanılacak Kütüphanelerin Yüklenmesi](#4-kullanılacak-kütüphanelerin-yüklenmesi)
  - [4.1. beautifulsoup4](#41-beautifulsoup4)
  - [4.2. requests](#42-requests)
  - [4.3. lxml](#43-lxml)
- [5. Örnek Web Sitesi Üzerinden Web Kazıma](#5-örnek-web-sitesi-üzerinden-web-kazıma)
  - [5.1. BeautifulSoup ve requests Kullanarak Web Kazıma](#51-beautifulsoup-ve-requests-kullanarak-web-kazıma)
    - [5.1.1. Örnek Web Sitesinin Oluşturulması](#511-örnek-web-sitesinin-oluşturulması)
    - [5.1.2. Kütüphanelerin Çağrılması](#512-kütüphanelerin-çağrılması)
    - [5.1.3. Örnek Olarak Oluşturulan Web Sitesini Kazıma](#513-örnek-olarak-oluşturulan-web-sitesini-kazıma)
      - [5.1.3.1. HTML Sayfasının Okunması](#5131-html-sayfasının-okunması)
      - [5.1.3.2. HTML Sayfasının Kazınması](#5132-html-sayfasının-kazınması)
- [6. Gerçek Hayat Uygulamaları](#6-gerçek-hayat-uygulamaları)
  - [6.1. BeautifulSoup ve requests Kullanarak Web Kazıma](#61-beautifulsoup-ve-requests-kullanarak-web-kazıma)
    - [6.1.1. IMDB](#611-imdb)
      - [6.1.1.1. İzin Durumunu Kontrol Etme](#6111-i̇zin-durumunu-kontrol-etme)
      - [6.1.1.2. IMDB'nin Kazınması](#6112-imdbnin-kazınması)
    - [6.1.2. Rotten Tomatoes](#612-rotten-tomatoes)
      - [6.1.2.1. İzin Durumunu Kontrol Etme](#6121-i̇zin-durumunu-kontrol-etme)
      - [6.1.2.2. Rotten Tomatoes'un Kazınması](#6122-rotten-tomatoesun-kazınması)

# 1. Web Kazıma (Web Scraping) Nedir?

---

Web kazıma (web scraping), web sitelerinden veya web uygulamalarından veri toplama işlemidir. Bu süreçte, bir web sayfasının HTML yapısı analiz edilir ve istenen veriler (genellikle tablo, liste, metin veya görüntü gibi) çekilerek bir veritabanına veya başka bir formata kaydedilir.

* Tablo örneği: Bir e-ticaret web sitesindeki ürünlerin fiyatları, stok durumu ve özelliklerini içeren bir tablo.
* Liste örneği: Bir haber web sitesindeki en son başlıkların bulunduğu bir liste.
* Metin örneği: Bir blog sitesindeki makalelerin içeriği.
* Görüntü örneği: Bir e-ticaret web sitesindeki ürün resimleri.

# 2. Web Kazıma Önlemleri

---

## 2.1. Neden Önlem Alınıyor?

* Veri Güvenliği: Web siteleri, kullanıcı verilerinin güvenliğini ve gizliliğini korumak için önlemler alır. Web kazıma, bu verilerin otomatik olarak toplanmasına ve kötü niyetli amaçlarla kullanılmasına yol açabilir. Örneğin, bir online alışveriş sitesi, kullanıcıların kredi kartı bilgileri gibi hassas verilerini korumak için güvenlik önlemleri alır. Bir kötü niyetli kişi veya program, web kazıma yöntemlerini kullanarak bu kullanıcı verilerini otomatik olarak toplayarak bu bilgileri kötüye kullanabilir.
* Telif Hakkı ve Fikri Mülkiyet: Web siteleri, içeriklerinin telif hakkını ve fikri mülkiyetini korumak ister. Web kazıma, bu içeriğin izinsiz olarak kopyalanmasına ve dağıtılmasına neden olabilir. Örneğin, bir haber web sitesi, kendi bünyesinde ürettiği haberleri ve makaleleri telif hakkı ile korur. Başka bir kişi veya program, web kazıma ile bu içerikleri izinsiz olarak kopyalayıp başka bir yerde yayınlarsa, bu web sitesinin telif hakkı ihlal edilmiş olur.
* Web Sunucusu Yükü: Web kazıma işlemleri büyük miktarda talep ve veri trafiği oluşturabilir ve web sunucularını aşırı yükleme riski taşır. Bu, web sitelerinin performansını düşürebilir ve kullanıcı deneyimini olumsuz etkileyebilir. Örneğin, popüler bir e-ticaret sitesi, bir indirim etkinliği sırasında yoğun bir şekilde ziyaretçi çeker. Bir kişi veya program, bu web sitesine aynı anda çok sayıda talep göndererek web kazıma yapmaya çalışırsa, sunucular aşırı yüklenebilir ve web sitesi yavaşlayabilir veya tamamen çökebilir.
* Rekabet: Web siteleri, rekabetçi bir ortamda faaliyet gösterir ve kendilerini diğer rakiplerinden ayırmak ister. Web kazıma, rakiplerin verileri otomatik olarak toplamalarına ve pazar analizleri yapmalarına olanak tanır. Örneğin, bir otel rezervasyon sitesi, rakiplerinin fiyatlandırma politikalarını ve müşteri tercihlerini analiz etmek için web kazıma kullanabilir. Bu sayede, rakiplerinin sunduğu fiyatları, müsaitlik durumlarını ve diğer verileri otomatik olarak toplayarak kendilerini rekabetin içinde avantajlı hale getirebilirler.
* Veri Manipülasyonu: Web kazıma, verilerin toplanmasını ve manipülasyonunu kolaylaştırır. Bu, yanlış veya yanıltıcı bilgilerin yayılmasına ve manipülasyonunun yapılmasına neden olabilir. Örneğin, bir siyasi haber sitesi, web kazıma yöntemlerini kullanarak anket sonuçlarını manipüle edebilir. Örneğin, sahte hesaplar üzerinden otomatik olarak anketlere katılım sağlayarak, sonuçları istedikleri şekilde değiştirebilir ve yanlış veya yanıltıcı bir tablo sunabilirler.

## 2.2. Hangi Önlemler Alınıyor?

Web kazımaya karşı alınabilecek bazı yaygın önlemlere bakalım.

* Robots.txt dosyası: Web sitesi sahipleri, web kazıma botlarına hangi sayfaların erişilebileceğini belirlemek için `robots.txt` dosyası kullanabilir. Bu dosyada, belirli botların veya tüm botların hangi sayfalara erişebileceği veya erişemeyeceği belirtilir. Web kazıma botları genellikle bu dosyayı kontrol eder ve talimatlara uyar. Örneğin, bir site sahibi tüm web kazıma botlarının blog sayfalarına erişmesini engellemek isteyebilir ve `robots.txt` dosyasında `/blog` dizinine erişimi engelleyici talimatlar ekleyebilir.

IMDB örneğine bakalım:

![](/imgs/imdb_robots_txt.PNG)

Bazı kısıtlamaların anlamları:

"User-agent: *" ifadesi, tüm botların aşağıdaki kısıtlamalara tabi olacağını belirtir.

"Disallow: /OnThisDay" ifadesi, "/OnThisDay" dizinini tarayan botlara erişimi engeller.

"Disallow: /ads/" ifadesi, "/ads/" dizinini tarayan botlara erişimi engeller.

"Disallow: /ap/" ifadesi, "/ap/" dizinini tarayan botlara erişimi engeller.

"Disallow: /mymovies/" ifadesi, "/mymovies/" dizinini tarayan botlara erişimi engeller.

...

* IP Adresi Engelleme: Web sitesi sahipleri, web kazıma faaliyetlerini tespit etmek için belirli IP adreslerini izleyebilir ve istenmeyen botların erişimini engelleyebilir. Örneğin, bir web sitesi sahibi birçok talep yapan ve hızlı bir şekilde sayfalara erişen bir IP adresini tespit ederse, bu IP adresini engelleyebilir ve bu botun web sitesine erişmesini önleyebilir.
* CAPTCHA: Bazı web siteleri, kullanıcıların insan olup olmadığını doğrulamak için CAPTCHA (Completely Automated Public Turing test to tell Computers and Humans Apart) gibi mekanizmalar kullanır. Bu, otomatik botların web sitesine erişmesini zorlaştırır ve web kazımını önleyebilir. Örneğin, bir kullanıcı bir formu göndermek veya bir hesap oluşturmak istediğinde, CAPTCHA doğrulaması yaparak botların otomatik olarak bu eylemleri gerçekleştirmesini önleyebilir.
* Dinamik İçerik: Web sitesi sahipleri, web kazıma botlarının veri kazımayı zorlaştırmak için web sayfalarında dinamik içerik kullanabilir. Örneğin, bir web sitesi içeriği JavaScript ile oluşturulabilir ve botların içeriği anlaması ve toplaması zorlaşabilir. Botlar, JavaScript'i yürütemez veya içeriği dinamik olarak oluşturamazlar.
* Kullanıcı İzleme: Web sitesi sahipleri, kullanıcıların davranışlarını izleyen analitik araçlar kullanabilir. Anormal veya yoğun kazıma faaliyetleri tespit edilirse bu botları engellemek için önlemler alınabilir. Örneğin, bir web sitesi sahibi bir kullanıcının kısa süre içinde çok sayıda sayfaya hızla eriştiğini tespit ederse, bu kullanıcıyı bot olarak değerlendirebilir ve onu engelleyici önlemler alabilir.
* Hukuki Yöntemler: Web sitesi sahipleri, web kazıma faaliyetlerini yasaklayan kullanım şartları veya hizmet şartlarına sahip olabilir. Bu şartlara uymayan botları engellemek veya hukuki yollara başvurmak gibi hukuki önlemler alabilirler. Örneğin, bir sosyal medya platformu kullanıcılarının platformdaki verileri web kazıma ile toplamasını yasaklayan bir politikaya sahip olabilir. Eğer bir kullanıcı bu politikayı ihlal ederse, web sitesi sahibi hukuki yollara başvurabilir ve bu kullanıcıyı engelleyebilir veya yasal işlem başlatabilir.

Web kazıma ve web sitesi yönetimi dinamik bir süreç olduğundan web sitesi sahipleri sürekli olarak yeni önlemler geliştirebilir ve güncellemeler yapabilir.

# 3. Bilinmesinde Yarar Olacak Teknik Bilgiler

---

## 3.1. HTML Nedir?

HTML, HyperText Markup Language (HiperMetin İşaretleme Dili) olarak bilinen, web sayfalarının yapısını tanımlamak için kullanılan bir işaretleme dilidir. HTML, web tarayıcıları tarafından anlaşılabilen bir metin formatıdır ve web sayfalarının içeriğini, yapısını ve görüntülenme şeklini belirtmek için kullanılır. HTML, etiketlerden oluşan bir yapıya sahiptir. Etiketler, içerik parçalarını belirlemek için kullanılan işaretlerdir.

```html
<!DOCTYPE html>
<html>
<head>
  <title>Örnek HTML Sayfası</title>
</head>
<body>
  <h1>Merhaba, Dünya!</h1>
  <p>Basit bir HTML sayfasının örneği.</p>
  <img src="resim.jpg" alt="Örnek Resim">
  <a href="https://github.com/urazakgul">GitHub</a>
</body>
</html>
```

Yukarıdaki HTML kodu basit bir web sayfasının yapısını tanımlar ve bu basit yapıda başlık (`title`), başlık etiketi (`h1`), paragraf (`p`), resim (`img`) ve bağlantı (`a`) gibi çeşitli etiketler kullanıldı.

* `!DOCTYPE html`: Sayfanın HTML5 standardına uygun olduğunu belirtir.
* `html`: HTML belgesinin kök elementidir ve içerisinde diğer tüm elementleri barındırır.
* `head`: Sayfanın başlık bilgilerini içeren bölümdür. Tarayıcıya görüntülenmeyen meta verileri, stil tanımları ve diğer önemli bilgiler burada yer alır.
* `title`: Sayfa başlığını belirtir. Tarayıcı sekmesinde veya sayfa başlığında görüntülenir.
* `body`: Sayfanın görüntülenen içeriğini içeren bölümdür. Metin, resim, bağlantılar ve diğer öğeler burada yer alır.
* `h1`: Başlık etiketi, büyük bir başlık metnini temsil eder.
* `p`: Paragraf etiketi, bir metin paragrafını temsil eder.
* `img`: Resim etiketi, sayfaya bir resim ekler. `src` özelliği, resmin kaynak dosyasının URL'ini belirtir. `alt` özelliği ise resim için bir alternatif metin sağlar.
* `a`: Bağlantı etiketi, bir bağlantı oluşturur. href özelliği, bağlantının hedef URL'ini belirtir.
* Kapanış etiketleri `</>` ilgili açılış etiketlerinin `<>` sonlandırılmasını sağlar.

Bu örnek, temel HTML yapısını ve bazı yaygın kullanılan etiketleri göstermektedir. Tabi ki, daha karmaşık ve detaylı HTML dosyaları da oluşturabiliriz ancak bu örnek temel anlamda nasıl çalıştığını anlamamıza yardımcı olacaktır.

HTML'de bilmemiz gereken konulardan biri de `id` ve `class` kavramlarıdır. HTML'de `id` ve `class` iki farklı özniteliktir ve HTML elemanlarına kimlik vermek için kullanılırlar.

`id` özniteliği, bir HTML elemanına benzersiz bir kimlik atamak için kullanılır. Bir sayfada yalnızca bir elemana özgüdür ve aynı `id` değerine sahip birden fazla eleman olmamalıdır.

```html
<div id="my-div">
  Bu bir div örneğidir.
</div>
```

`class` özniteliği, bir veya daha fazla HTML elemanına aynı veya benzer özellikler eklemek için kullanılır. Bir sayfada birden fazla eleman aynı `class` değerine sahip olabilir.

```html
<p class="my-p">Bu bir paragraf örneğidir.</p>
<p class="my-p">Bu da başka bir paragraf örneğidir.</p>
```

## 3.2. XML Nedir?

XML, Extensible Markup Language (Genişletilebilir İşaretleme Dili) olarak bilinen, veri saklamak ve iletmek için kullanılan bir metin tabanlı bir işaret dilidir. XML, verileri yapılandırılmış bir şekilde depolamak, taşımak ve paylaşmak için kullanılır. Veriye odaklanan bir formatta olduğu için sıklıkla veri alışverişi, veri depolama ve belge oluşturma amaçlarıyla kullanılır.

```xml
<kitaplar>
  <kitap>
    <baslik>Harry Potter ve Felsefe Taşı</baslik>
    <yazar>J.K. Rowling</yazar>
    <yil>1997</yil>
  </kitap>
  <kitap>
    <baslik>1984</baslik>
    <yazar>George Orwell</yazar>
    <yil>1949</yil>
  </kitap>
</kitaplar>
```

Bu XML örneği, `kitaplar` isminde bir kök öğesi içerir. Kök öğesinin altında iki `kitap` öğesi bulunur. Her `kitap` öğesi, `baslik`, `yazar` ve `yil` isminde üç alt öğe içerir. Bu öğeler, her bir kitabın başlığını, yazarını ve yayınlanma yılını temsil eder.

## 3.3. HTTP Nedir? HTTP İstekleri Nelerdir?

HTTP, Hypertext Transfer Protocol (Hiper Metin Transfer Protokolü) olarak bilinen, web tarayıcıları ve web sunucuları arasında iletişim kurmak için kullanılan bir iletişim protokolüdür. Bu protokol, web tarayıcısının sunucudan web sayfalarını istemesi ve sunucunun bu isteklere cevap vermesi için kullanılır. HTTP, istemci-sunucu modeline dayanan bir protokoldür. İstemci, genellikle bir web tarayıcısıdır ve sunucu, web sayfalarını barındıran bir web sunucusudur. İstemci, sunucuya bir istek gönderir ve sunucu da bu isteği işler ve yanıt olarak istemciye bir yanıt gönderir.

![https://bytesofgigabytes.com/networking/how-http-request-and-response-works/](/imgs/http.PNG)

HTTP'nin temel istekleri şunlardır:

* GET: Sunucudan belirli bir kaynağı (web sayfası, resim, vb.) almak için kullanılır.
* POST: Sunucuya veri göndermek için kullanılır. Örneğin, bir formdaki verileri sunucuya göndermek için POST isteği kullanılır.
* PUT: Sunucuya yeni bir kaynak eklemek veya mevcut bir kaynağı güncellemek için kullanılır.
* DELETE: Sunucudan bir kaynağı silmek için kullanılır.
* HEAD: Sunucudan yalnızca yanıt başlığını almak için kullanılır. İçerik indirilmez.
* OPTIONS: Sunucunun desteklediği HTTP yöntemlerini ve diğer seçenekleri almak için kullanılır.

Bunlar, en yaygın kullanılan HTTP istekleridir. Her bir istek, sunucunun belirli bir eylem gerçekleştirmesini isteyen istemci tarafından gönderilir. Sunucu, isteği işler ve uygun yanıtı istemciye gönderir. Yanıtlar, isteğin başarılı bir şekilde gerçekleşip gerçekleşmediğini, hata durumlarını veya istenen içeriği içerebilir.

## 3.4. Web Kazımada Karşılaşılabilecek HTTP Durum Kodları

HTTP durum kodları (status codes) istemci ile sunucu arasındaki iletişimin sonucunu 3 haneli bir sayı ile ifade eder.

Yaygın olarak karşılaşılabilecek bazı HTTP durum kodlarının tanımları aşağıdaki gibidir.

* 200: İstek başarılı ve sunucu doğru yanıt verdi.
* 400: İstek geçersiz veya hatalı, sunucu isteği anlamadı.
* 403: Yasaklanmış, erişim reddedildi, istemci yetkilendirme eksikliği nedeniyle kaynaklara erişemiyor.
* 404: Bulunamadı, istemci istenen kaynağı sunucuda bulamadı.
* 429: İstek sınırı aşıldı, istemci belirli bir süre içinde çok fazla istekte bulundu.
* 500: Sunucu hatası, istemci isteği yerine getiremedi çünkü sunucuda bir iç hata oluştu.
* 503: Hizmet kullanılamıyor, sunucu geçici olarak bakım veya aşırı yükleme nedeniyle istemcilere hizmet veremiyor.

# 4. Kullanılacak Kütüphanelerin Yüklenmesi

---

## 4.1. beautifulsoup4

`beautifulsoup4`, Python programlama dilinde yaygın olarak kullanılan bir HTML ve XML analiz kütüphanesidir. Bu kütüphane, web kazıma işlemlerinde HTML veya XML dokümanlarını ayrıştırmak, veri çekmek ve manipüle etmek için kullanılır. `beautifulsoup4`, Python'ın `requests` kütüphanesi ile birlikte kullanılarak web sayfalarını indirebilir ve daha sonra bu indirilen sayfalar üzerinde analiz yapabilir. Ayrıca, diğer dosya biçimlerindeki verileri analiz etmek için de kullanılabilir.

```
pip install beautifulsoup4
```

## 4.2. requests

`requests`, Python programlama dilinde yaygın olarak kullanılan bir HTTP kütüphanesidir. Bu kütüphane, HTTP istekleri göndermek ve yanıtları almak için kullanılır. HTTP istekleri yapma, yanıtları işleme ve web servisleriyle etkileşim kurma gibi birçok HTTP tabanlı işlemi kolaylaştırır.

```
pip install requests
```

## 4.3. lxml

`lxml`, Python programlama dilinde XML ve HTML belgelerini işlemek için kullanılan popüler bir kütüphanedir.

```
pip install lxml
```

# 5. Örnek Web Sitesi Üzerinden Web Kazıma

---

## 5.1. BeautifulSoup ve requests Kullanarak Web Kazıma

### 5.1.1. Örnek Web Sitesinin Oluşturulması

HTML ile örnek bir blog sayfası yazalım. Bu örnek için bulunduğunuz klasöre bir tane `index.html` dosyası açabilirsiniz. Bu dosyanın içerisine aşağıdaki HTML kodlarını ekleyebilirsiniz. Siteyi görmek için ister bulunduğunuz klasördeki `index.html`'i tarayıcınız ile açın isterseniz de Visual Studio Code kullanıyorsanız `Live Server` eklentisini yükleyip bu eklentiyi kullanarak açın. Visual Studio Code içinde `index.html`'e sağ tıklayıp `Open with Live Server` seçeneğine tıklamanız yeterli olacaktır. Şu aşamada pek ihtiyacımız olmasa da bu eklenti aynı zamanda değişiklikleri anlık olarak gösteriyor.

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Yunan Mitolojisi Blogu</title>
</head>
<body>
  <h1>Yunan Mitolojisi Blogu</h1>

  <hr>

  <div class="blog-post">
    <h2 class="blog-title"><a href="https://tr.wikipedia.org/wiki/Zeus" target="_blank">Zeus</a>: Tanrıların Kralı</h2>
    <p class="blog-date">Yayınlanma Tarihi: 07 Temmuz 2023</p>
    <p class="blog-content">
      Zeus, Yunan mitolojisinde en güçlü tanrı olan ve Olimpos Dağı'nda yaşayan tanrılara hükmeden tanrıdır. O, gökyüzünün ve yıldırımların tanrısıdır. Zeus'un babası Kronos'tu ve o da babası Uranos'u devirmişti. Bu şekilde Zeus, Olimpos Dağı'nda hüküm süren bir tanrı haline gelmiştir.
    </p>
  </div>

  <hr>

  <div class="blog-post">
    <h2 class="blog-title"><a href="https://tr.wikipedia.org/wiki/Athena" target="_blank">Athena</a>: Savaş Tanrıçası</h2>
    <p class="blog-date">Yayınlanma Tarihi: 08 Temmuz 2023</p>
    <p class="blog-content">
      Athena, Yunan mitolojisinde bilgelik, strateji, savaş ve sanatın tanrıçası olarak bilinir. Aynı zamanda Athena, şehirlerin koruyucusu olarak da saygı görür. Athena, savaşta akıl ve stratejiyi kullanırken, sanat ve zanaatın da tanrıçasıdır. Heykellerde genellikle bir miğfer ve kalkanla tasvir edilir.
    </p>
  </div>

  <hr>

  <div class="blog-post">
    <h2 class="blog-title"><a href="https://tr.wikipedia.org/wiki/Poseidon" target="_blank">Poseidon</a>: Deniz Tanrısı</h2>
    <p class="blog-date">Yayınlanma Tarihi: 09 Temmuz 2023</p>
    <p class="blog-content">
      Poseidon, Yunan mitolojisinde denizlerin, depremlerin ve atların tanrısıdır. Olimpos Dağı'nda Zeus ve Hades ile birlikte hüküm sürer. Poseidon, ünlü üç dişli mızrağı ile bilinir ve denizlerin sularını kontrol edebilir. Aynı zamanda atların yaratıcısı olarak da saygı görür.
    </p>
  </div>

  <hr>

</body>
</html>
```

Blog sayfasına ait ekran görüntüsü aşağıdaki gibi olacaktır.

![](/imgs/blog.PNG)

Blog sayfasında herhangi bir yere sağ tıklayıp `İncele` dediğimizde ya da `F12` klavye tuşuna bastıktan sonra `Elements` başlığına geldiğimizde yazdığımız HTML kodlarını görmüş olacağız.

![](/imgs/blog_html.PNG)

### 5.1.2. Kütüphanelerin Çağrılması

```python
from bs4 import BeautifulSoup
import requests
```

### 5.1.3. Örnek Olarak Oluşturulan Web Sitesini Kazıma

#### 5.1.3.1. HTML Sayfasının Okunması

```python
with open('index.html', encoding='utf-8') as html_dosyasi:
    soup = BeautifulSoup(html_dosyasi, 'lxml')

print(soup)
```

![](/imgs/blog_soup.PNG)

Yukarıdaki kod, `BeautifulSoup`'u kullanarak bir HTML dosyasını analiz etmeyi sağlıyor. Neler yaptığımıza bakalım.

* İlk satırda, `open()` fonksiyonu kullanarak `index.html` isimli bir HTML dosyası açtık. `open()` fonksiyonu, belirtilen dosyayı okumak için bir dosya nesnesi döndürür ve bu nesne `html_dosyasi` ismiyle atanır. `open()` fonksiyonuna aynı zamanda `encoding='utf-8'` parametresini ekleyerek Türkçe karakterleri de tanımasını sağlattırdık.
* İkinci satırda, `BeautifulSoup` sınıfı kullanılarak `html_dosyasi` dosyası `soup` isimli bir nesneye dönüştürülüyor. Bu nesne, `BeautifulSoup` tarafından sunulan özelliklere ve yöntemlere erişim sağlar. `BeautifulSoup` sınıfının ilk parametresi, analiz edilecek dosya veya metin olabilir. Bu örnekte, `html_dosyasi` değişkeni, analiz edilecek HTML dosyasını temsil ediyor. İkinci parametre olarak `'lxml'` belirtiliyor, bu da `BeautifulSoup`'un analiz etmek için `lxml` `parser`'ını kullanacağını belirtiyor.
* Üçüncü satır, analiz edilen HTML içeriğini yazdırmak için kullanılır. `print(soup)` ifadesi, `soup` nesnesinin string temsilini yazdırır. Bu, analiz edilen HTML yapısını düzenli bir biçimde görüntüler.

Yukarıdaki koda `prettify()` da eklenebilir. `prettify()` fonksiyonu, `BeautifulSoup` tarafından sağlanan bir yöntemdir ve analiz edilen HTML belgesini daha okunabilir bir biçimde düzenler

```python
with open('index.html', encoding='utf-8') as html_dosyasi:
    soup = (BeautifulSoup(html_dosyasi, 'lxml')).prettify()

print(soup)
```

![](/imgs/blog_soup_prettify.PNG)

#### 5.1.3.2. HTML Sayfasının Kazınması

```python
with open('index.html', encoding='utf-8') as html_dosyasi:
    soup = BeautifulSoup(html_dosyasi, 'lxml')
```

`title`'ı alalım.

```python
baslik = soup.title
print(baslik)
```

`title` değerini atadığımız `baslik` değişkenini çalıştırdığımızda `<title>Yunan Mitolojisi Blogu</title>` çıktısını alacağız. Ancak biz `title` etiketini istemiyoruz. Bu etiketin içindeki metin ile ilgileniyoruz.

```python
baslik = soup.title.text
print(baslik)
```

`title` etiketi içerisinde bulunan metni `text` ile alıp ardından atadığımız `baslik` değişkenini çalıştırdığımızda `Yunan Mitolojisi Blogu` çıktısına ulaşıyoruz.

`div`'i alalım.

```python
div_etiket = soup.div
print(div_etiket)
```

![](/imgs/blog_div_tag.PNG)

Ancak bizim birden fazla `div` etiketimiz bulunmaktadır. Bize sadece ilkini verdi. Bu noktada `find()` fonksiyonuna bakalım. Bu fonksiyon ile yine aynı çıktıyı alacağız ama istediğimiz `div` etiketine ulaşabileceğiz.

```python
div_spesifik = soup.find('div', class_='blog-post')
print(div_spesifik)
```

![](/imgs/blog_div_tag.PNG)

Burada ek olarak `class`'ı da belirttik. Ancak bunu alt çizgi ile yazdık çünkü class Python'da bir anahtar kelimedir (keyword).

Eğer `class`'ı farklı olan bir `div` olsaydı ve biz onu yazsaydık, çıktı olarak belirttiğimiz `div`'i alacaktık.

Eğer aynı `class`'a sahip birden fazla `div`'e ulaşmak istiyorsak bu defa `find_all()` fonksiyonunu kullanabiliriz.

```python
div_spesifik_hepsi = soup.find_all('div', class_='blog-post')
print(div_spesifik_hepsi)
```

![](/imgs/blog_div_tag_all.PNG)

Blog sayfasındaki başlıkları almak isteyelim. Bundan sonra artık istediğimiz bilgilere erişebilmeyi de görelim.

Blog sayfasına gidip ilk başlığın üzerine sağ tıklayıp `İncele` diyelim.

![](/imgs/blog_h2_inspect.PNG)

`İncele` seçeneğine tıkladıktan sonra `h2` etiketinin nereye denk geldiğini görebiliriz.

![](/imgs/blog_h2_detail.PNG)

`class`'ları kullanırken `.`; `ìd`'leri kullanırken `#` ile işlem yapacağız. Yukarıdaki örnek bir `class` olduğu için `.blog-title` olarak görülmektedir.

Öncesinde, bu başlığın içinde yer aldığı `div`'i alalım. Web kazımada bir hiyerarşiyi takip etmek faydalıdır.

![](/imgs/blog_div_inspect.PNG)

```python
konu_div = soup.find('div', class_='blog-post')
print(konu_div)
```

![](/imgs/blog_div_tag.PNG)

Buradan artık konu başlığına ulaşabiliriz. Artık `soup`'u değil; `konu_div` değişkenini kullanacağız.

```python
konu_baslik = konu_div.h2.text
print(konu_baslik)
```

`konu_div` değişkeninin içindeki `h2` etiketinde bulunan metni `text` ile aldık. Blog sayfasında dikkat edilirse tanrı isimlerinin altı çizili ve renkli. Çünkü biz bu isimleri bir `a` etiketinin içine aldık. `a` etiketinin içine alınan metinlere tıklanabilir ve farklı bir kaynağa gidilebilir. Biz örnek olarak aşağıdan da görüleceği üzere her tanrının Vikipedi sayfalarını girdik.

![](/imgs/blog_h2_a_inspect.PNG)

Eğer konu başlıklarındaki sadece `a` etiketi içerisinde bulunan isimleri almak isteseydik aşağıdaki kodu çalıştıracaktık.

```python
konu_baslik_a = konu_div.h2.a.text
print(konu_baslik_a)
```

Çıktıyı `Zeus` olarak alacağız.

Hızlıca paragrafa da ulaşalım.

```python
konu_paragraf = konu_div.p.text
print(konu_paragraf)
```

Eğer yukarıdaki kodu çalıştırırsak `Yayınlanma Tarihi: 07 Temmuz 2023` çıktısını alacağız. Çünkü ilgili `div`'in içerisinde iki tane `p` etiketi bulunmaktadır.

![](/imgs/blog_div_tag.PNG)

Bu yöntemle erişmek istediğimizde ise ilkini dikkate almaktadır. Bu noktada `find_all()` fonksiyonunu ve `if else` koşul ifadelerini kullanabiliriz.

```python
konu_p_liste = konu_div.find_all('p')
print(konu_p_liste)
```

![](/imgs/blog_p_list.PNG)

Tüm `p` etiketlerini aldık. Şimdi bir koşul ifadesi girelim.

```python
if len(konu_p_liste) > 1:
    ikinci_p = konu_p_liste[1]
    konu_paragraf = ikinci_p.text
    print(konu_paragraf)
else:
    print('Birden fazla p etiketi bulunmamaktadır.')
```

Kodu çalıştırdığımızda *`Zeus, Yunan mitolojisinde en güçlü tanrı olan ve Olimpos Dağı'nda yaşayan tanrılara hükmeden tanrıdır. O, gökyüzünün ve yıldırımların tanrısıdır. Zeus'un babası Kronos'tu ve o da babası Uranos'u devirmişti. Bu şekilde Zeus, Olimpos Dağı'nda hüküm süren bir tanrı haline gelmiştir.`* çıktısını almış olacağız.

Tek bir başlık yerine tüm başlıkları alalım. Bir `for` döngüsü ile bunu yapabiliriz.

```python
for post in soup.find_all('div', class_='blog-post'):
    baslik = post.h2.text

    p_liste = post.find_all('p')
    if len(p_liste) > 1:
        ikinci_p = p_liste[1]
        paragraf = ikinci_p.text

        print(baslik)
        print(paragraf)
        print('*'*30)
```

![](/imgs/blog_post_h2_p.PNG)

# 6. Gerçek Hayat Uygulamaları

---

## 6.1. BeautifulSoup ve requests Kullanarak Web Kazıma

```python
from bs4 import BeautifulSoup
import requests
```

### 6.1.1. IMDB

#### 6.1.1.1. İzin Durumunu Kontrol Etme

Web kazıma için kullanacağımız IMDB'nin izin durumunu kontrol edelim. Bunu iki yoldan yapabiliriz.

Birincisi, `https://www.imdb.com/robots.txt` URL'ini kopyaladıktan sonra tarayıcıya yapıştırıp çalıştırmaktır. Aşağıdaki gibi bir ekran ile karşılacağız.

![](/imgs/imdb_robots_txt.PNG)

Bizim ilgileneceğimiz URL, Most Popular TV Shows'un olduğu `https://www.imdb.com/chart/tvmeter/?ref_=nv_tvv_mptv`.

Burada URL yerine dizin ile ilgileniyoruz. İlgileneceğimiz dizin `/chart/tvmeter/?ref_=nv_tvv_mptv` olacak. Belki daha da genelleştirip `/chart/` dizinine de bakabiliriz.

Görüntüde böyle bir engel yok. Bir de ikinci bir yol olarak Python ile bakalım.

```python
url = 'https://www.imdb.com/robots.txt'
response = requests.get(url)
robots_txt = response.text

if '/chart/' in robots_txt:
    print('İzin Yok')
else:
    print('İzin Var')
```

Çıktıyı `İzin Var` olarak aldık.

#### 6.1.1.2. IMDB'nin Kazınması

![](/imgs/imdb_list.PNG)

Buradan dizilerin isimlerini, yapım senelerini, puanlarını ve her bir dizinin URL'ini alalım.

```python
kaynak = requests.get('https://www.imdb.com/chart/tvmeter/?ref_=nv_tvv_mptv')
print(kaynak)
```

Yukarıda `requests` yardımıyla bir HTTP GET isteği gönderildi. İstek, `https://www.imdb.com/chart/tvmeter/?ref_=nv_tvv_mptv` adresine yapıldı ve yanıt alındı. Yanıt, `kaynak` isimli bir değişkene atanarak saklandı.

Önceden planlanmamış bir şekilde hazırladığım için doğal süreçleri de derslerde bırakmak istiyorum. Örneğin, yukarıdaki URL'e istek gönderirken `<Response [403]>` alıyoruz. 403 kodu, HTTP isteğinin sunucu tarafından reddedildiğini ve istemcinin erişim iznine sahip olmadığını belirtir.

İznimiz olan başka bir web sitesi ve uygulamaya geçelim.

### 6.1.2. Rotten Tomatoes

#### 6.1.2.1. İzin Durumunu Kontrol Etme

`https://www.rottentomatoes.com/robots.txt`'yi incelediğimizde erişmek istediğimiz `https://www.rottentomatoes.com/browse/tv_series_browse/affiliates:netflix~sort:popular` URL'i (ve dizini) için herhangi bir engel görmüyoruz.

```
User-agent: *
Disallow: /search
Disallow: /user/id/
Sitemap: https://www.rottentomatoes.com/sitemaps/sitemap.xml
```

#### 6.1.2.2. Rotten Tomatoes'un Kazınması

İstek gönderelim ve HTTP durum kodunu alalım.

```python
kaynak = requests.get('https://www.rottentomatoes.com/browse/tv_series_browse/affiliates:netflix~sort:popular')
print(kaynak)
```

Durum kodu `<Response [200]>` olarak döndü ki bu da isteğin başarılı olduğunu gösteriyor.

![](/imgs/rottentomatoes_list.PNG)

Buradan dizilerin isimlerini, son bölümün tarihini, puanlarını ve her bir dizinin URL'ini alalım.

```python
soup = BeautifulSoup(kaynak.content, 'lxml')
print(soup.prettify())
```

![](/imgs/rottentomatoes_content.PNG)

`kaynak.content` özelliğini kullanarak Response objesinin içeriğine eriştik.

Tabi bu ekran pek bir anlam ifade etmiyor. Sadece istek gönderip içeriği alabildiğimizi gördük.

Dizi isminin üzerine sağ tıklayıp incelemeye alalım.

![](/imgs/rottentomatoes_title.PNG)

Dizinin `js-tile-link` `class`'ına sahip bir `div`'in içinde olduğunu görüyoruz. Önce bu `div`'i alalım.

```python
dizi_div = soup.find('div', class_='js-tile-link')
print(dizi_div.prettify())
```

![](/imgs/rottentomatoes_div_series.PNG)

Ardından buradan `a` etiketini alabiliriz. Çünkü dizi ismi, son bölüm tarihi, puanlar bu etiketin altında yer alıyor.

![](/imgs/rottentomatoes_div_series_a.PNG)

```python
dizi_div_a = dizi_div.a
print(dizi_div_a.prettify())
```

![](/imgs/rottentomatoes_div_series_a_2.PNG)

Artık dizi ismini `text` ile direkt olarak alabiliriz. Ama öncesinde `span` etiketine erişeceğiz.

![](/imgs/rottentomatoes_div_a_span_1.PNG)

```python
dizi_ismi = dizi_div_a.span.text
print(dizi_ismi)
```

Çıktıyı `The Witcher` olarak aldık. Hemen buradan dizinin son bölüm tarihini de alabiliriz. Ancak dizinin ismi de tarih de `span` etiketleri arasında.

![](/imgs/rottentomatoes_div_a_span_2.PNG)

Bu durumda, `find_all()` kullanabiliriz. Bu fonksiyon ile `span` içerisindeki her iki bilgiyi de alalım.

```python
dizi_ismi = dizi_div_a.find_all('span')[0].text
print(dizi_ismi)

dizi_son_tarih = dizi_div_a.find_all('span')[1].text
print(dizi_son_tarih)
```

Çıktılarımız sırasıyla, `The Witcher` ve `Latest Episode: Jun 29` olacak.

Geldik puanları alma aşamasına.

Rotten Tomatoes, film ve televizyon programlarının eleştirel derecelendirmelerini toplayan ve bu değerlendirmeleri kullanarak bir filmin veya dizinin taze (fresh) veya çürümüş (rotten) olduğunu belirleyen bir web sitesidir. Rotten Tomatoes'un puanlama sistemi iki ana bileşenden oluşur: Tomatometer ve Audience Score. Tomatometer, eleştirel incelemeleri toplar ve bir filmin veya dizinin taze veya çürümüş olarak nitelendirilmesi için gereken yüzdeyi belirler. Audience Score, seyircilerin filmleri veya dizileri nasıl değerlendirdiğini gösteren bir puanlama sistemidir.

Puanların `score-pairs` isimli bir etiketin içerisinde olduğunu görüyoruz.

![](/imgs/rottentomatoes_div_a_score_pairs.PNG)

Her iki skoru da alalım.

```python
skorlar = dizi_div_a.find('score-pairs')

elestirmen_skoru = skorlar['criticsscore']
print(elestirmen_skoru)

seyirci_skoru = skorlar['audiencescore']
print(seyirci_skoru)
```

Çıktılarımız sırasıyla `82` ve `60` olacak.

Son olarak her bir dizinin URL'ini alalım. Bunu direkt olarak `a` etiketi içerisindeki `href` özniteliği ile alabiliriz.

![](/imgs/rottentomatoes_div_a_href.PNG)

```python
dizi_url = dizi_div.find('a')['href']
print(dizi_url)
```

Burada, `dizi_div_a` yerine bir üstü olan `dizi_div`'i kullandık. Çıktımız `/tv/the_witcher` olacaktır. Tabi bu şekilde pek işe yaramayacaktır. Bunu, `https://www.rottentomatoes.com/tv/the_witcher` olarak değiştirmemiz gerekiyor. Yani, `https://www.rottentomatoes.com` ile `/tv/the_witcher` birleştirilecek.

İstediğimiz tüm bilgilere ulaşmış olduk. Artık bunu tüm diziler için yapmamız ve bilgileri bir veri çerçevesinde saklamamız gerekiyor. Ardından da verileri istediğimiz formatta dışarı aktarabiliriz.

```python
from bs4 import BeautifulSoup
import requests
import pandas as pd

baz_url = 'https://www.rottentomatoes.com'

kaynak = requests.get(baz_url + '/browse/tv_series_browse/affiliates:netflix~sort:popular')
soup = BeautifulSoup(kaynak.content, 'lxml')
dizi_divler = soup.find_all('div', class_='js-tile-link')

df = pd.DataFrame(columns=['Isim', 'Son_Tarih', 'Elestirmen_Skor', 'Seyici_Skor', 'URL'])

for dizi_div in dizi_divler:
    dizi_div_a = dizi_div.a

    dizi_ismi = dizi_div_a.find_all('span')[0].text.strip() # \n'leri kaldırmak için.

    dizi_son_tarih = ''
    # IndexError: list index out of range almamak için koşul
    if len(dizi_div_a.find_all('span')) > 1:
        dizi_son_tarih = dizi_div_a.find_all('span')[1].text.strip() # \n'leri kaldırmak için.

    skorlar = dizi_div_a.find('score-pairs')
    elestirmen_skoru = skorlar['criticsscore']
    seyirci_skoru = skorlar['audiencescore']

    dizi_url = baz_url + dizi_div.find('a')['href']

    df_alt = pd.DataFrame({
            'Isim': [dizi_ismi],
            'Son_Tarih': [dizi_son_tarih],
            'Elestirmen_Skor': [elestirmen_skoru],
            'Seyici_Skor': [seyirci_skoru],
            'URL': [dizi_url]
    })

    df = pd.concat([df, df_alt.reset_index(drop=True)], ignore_index=True)

df
```

![](/imgs/rottentomatoes_netflix_list_page1.PNG)

Web sitesinde sayfanın sonunda `Load More` butonu göreceksiniz. Eğer bu butona tıklarsanız URL `https://www.rottentomatoes.com/browse/tv_series_browse/affiliates:netflix~sort:popular?page=2` olarak güncellenecektir. Yani, ilk URL'imizden farklı olarak `?page=2` eklenecek. Aslında bu durumda `?page=1` ilk baktığımız URL oluyor. Son olarak, `Load More` butonuna her tıkladığımızda `page`'in değeri artacaktır.

Bu uygulamada sadece 2 sayfanın nasıl kazınabileceğini göreceğiz. Sayfa sayısı kodun içerisinden artırılabilir.

```python
from bs4 import BeautifulSoup
import requests
import pandas as pd

baz_url = 'https://www.rottentomatoes.com/browse/tv_series_browse/affiliates:netflix~sort:popular?page='
sayfa_sayisi = 2  # İstediğiniz sayfa sayısını burada belirleyebilirsiniz

df = pd.DataFrame(columns=['Isim', 'Son_Tarih', 'Elestirmen_Skor', 'Seyici_Skor', 'URL'])

for sayfa in range(1, sayfa_sayisi + 1):
    kaynak = requests.get(baz_url + str(sayfa))
    soup = BeautifulSoup(kaynak.content, 'lxml')
    dizi_divler = soup.find_all('div', class_='js-tile-link')

    for dizi_div in dizi_divler:
        dizi_div_a = dizi_div.a

        dizi_ismi = dizi_div_a.find_all('span')[0].text.strip() # \n'leri kaldırmak için.

        dizi_son_tarih = ''
        # IndexError: list index out of range almamak için koşul
        if len(dizi_div_a.find_all('span')) > 1:
            dizi_son_tarih = dizi_div_a.find_all('span')[1].text.strip() # \n'leri kaldırmak için.

        skorlar = dizi_div_a.find('score-pairs')
        elestirmen_skoru = skorlar['criticsscore']
        seyirci_skoru = skorlar['audiencescore']

        dizi_url = baz_url + dizi_div.find('a')['href']

        df_alt = pd.DataFrame({
            'Isim': [dizi_ismi],
            'Son_Tarih': [dizi_son_tarih],
            'Elestirmen_Skor': [elestirmen_skoru],
            'Seyici_Skor': [seyirci_skoru],
            'URL': [dizi_url]
        })

        df = pd.concat([df, df_alt.reset_index(drop=True)], ignore_index=True)

df.tail(10)
```

![](/imgs/rottentomatoes_netflix_list_page2.PNG)

Son veriyi `.xlsx` formatında dışarı aktaralım.

```python
df.to_excel('./RottenTomatoesNetflixTvShows.xlsx', index=False)
```