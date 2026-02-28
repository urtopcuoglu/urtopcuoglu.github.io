# CSS Vendor Prefix Hataları İçin Çözüm

## Sorun
IDE modern CSS syntax'ını bildiği için eski vendor prefix'leri (`-webkit-`, `-moz-`, `-ms-`) anlayamıyor ve hata gösteriyor.

## Çözümler

### 1. JetBrains IDE (WebStorm, IntelliJ IDEA, PHPStorm vb.)

Zaten yapılandırıldı! `.idea/inspectionProfiles/Project_Default.xml` dosyası CSS kontrollerini devre dışı bırakıyor.

**IDE'yi yeniden başlatın** veya şu adımları izleyin:
1. `File` > `Invalidate Caches / Restart...`
2. `Invalidate and Restart` seçeneğini seçin

### 2. Visual Studio Code

`.vscode/settings.json` dosyası zaten oluşturuldu ve CSS doğrulamayı kapatıyor.

### 3. Manuel Ayar (JetBrains IDE)

1. `Settings/Preferences` > `Editor` > `Inspections`
2. `CSS` bölümünü genişletin
3. Şu kontrolleri devre dışı bırakın:
   - Unknown CSS property
   - Invalid property value
   - Overwritten properties
   - Redundant unit

## Neden Bu Prefix'ler Kullanılıyor?

Bu vendor prefix'ler eski tarayıcı desteği için gereklidir:
- `-webkit-`: Chrome, Safari, Edge (eski sürümler)
- `-moz-`: Firefox
- `-ms-`: Internet Explorer, Edge (eski sürümler)

Modern tarayıcılar bu özellikleri desteklese de, eski cihaz/tarayıcı kullanan ziyaretçiler için bu prefix'ler önemlidir.

## Autoprefixer Kullanımı

Projede `gulp-autoprefixer` zaten mevcut. CSS'i derlerken otomatik olarak gerekli prefix'leri ekler:

```bash
npm run build  # veya
gulp build
```

## Geliştirme Süreci

1. SASS dosyalarını düzenleyin (`app/sass/`)
2. Gulp ile derleyin: `gulp` veya `npm run dev`
3. Autoprefixer otomatik olarak prefix'leri ekleyecektir

## Notlar

- CSS dosyalarını (`app/css/`) doğrudan düzenlemeyin, SASS dosyalarını kullanın
- IDE hataları görsel olarak rahatsız edici olabilir ama bunlar kodun çalışmasını etkilemez
- Modern projelerde vendor prefix'ler genelde otomatik araçlarla eklenir

