# Maintainer: Attila Bukor <r1pp3rj4ck [at] w4it [dot] eu>

pkgname=gush
pkgver=1.3.8
pkgrel=2
pkgdesc="Rapid workflow for GitHub project maintainers and contributors"
url="http://gushphp.org"
arch=('x86_64' 'i686')
license=('mit')
makedepends=('php-box' 'php-composer')
depends=('php')
source=("https://github.com/gushphp/gush/archive/v${pkgver}.tar.gz"
  "https://github.com/gushphp/gush/blob/v${pkgver}/LICENSE"
  'box.json.dist.patch'
  'Application.php.patch')
md5sums=('50fb6c842c1edc38189c49b8c47a8a19'
         '3eeb024c10db7d53b0ead6f1e702ea3b'
         '1ac5c23f8ec3a91f18066d1ab591a215'
         'ab531d50ac9577b15b18c17729d3b2e5')

build() {
  cd ${srcdir}/gush-${pkgver}
  composer install --no-dev
  patch -p0 <../../box.json.dist.patch
  patch -p0 <../../Application.php.patch
  php-box build
}

package() {
  install -D -m 644 ${srcdir}/LICENSE ${pkgdir}/usr/share/licenses/${pkgname}/license.txt
  install -D -m 755 ${srcdir}/gush-${pkgver}/gush.phar ${pkgdir}/usr/share/webapps/bin/gush.phar
  install -d ${pkgdir}/usr/bin
  ln -s /usr/share/webapps/bin/gush.phar ${pkgdir}/usr/bin/gush
}

# vim:set ts=2 sw=2 et: