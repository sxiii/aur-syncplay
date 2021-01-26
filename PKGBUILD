pkgname=syncplay
_pkgver=1.6.7
pkgver=${_pkgver//-/.}
pkgrel=1
pkgdesc="synchronize watching movies on mplayer2, vlc, mpv, and mpc-hc on many computers"
arch=('any')
url="http://syncplay.pl/"
license=('Apache')
depends=('python' 'python-twisted')
optdepends=('pyside2: GUI' 'qt5-declarative: GUI' 'python-service_identity: TLS' 'python-certifi: TLS')
provides=(${pkgname})
conflicts=(${pkgname})
replaces=()
backup=("etc/syncplay/server.conf")
source=("https://github.com/Syncplay/syncplay/archive/v${_pkgver}.tar.gz"
        'syncplay@.service'
        server.conf)
sha256sums=('2b9329bf8abbaa810bea07bf4743684d77565ae036abbbb259fecd506d52748a'
            'bbbf8f9dfc36631b49ba7d0fe3f980066b30a544954680a677e5e8629b7e0a8b'
            'df3c7656024d60c59664c79f4890f7780a2c5b8b537ac61b017e16b3d4420808')
install=syncplay.install
package() {
  cd $srcdir

  # systemd unit and its config file
  install -Dm644 syncplay@.service ${pkgdir}/usr/lib/systemd/system/syncplay@.service
  install -Dm644 server.conf "$pkgdir"/etc/syncplay/server.conf

  cd "syncplay-${_pkgver}"

  make DESTDIR="$pkgdir" install
}
