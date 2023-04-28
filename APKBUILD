# Contributor: Wouter van der Wal <me@wjtje.dev>
# Maintainer: Wouter van der Wal <me@wjtje.dev>
pkgname=openocd-esp32
pkgver=0.12.0
pkgrel=0
pkgdesc="OpenOCD provides on-chip programming and debugging support with a layered architecture of JTAG interface and TAP support"
url="https://github.com/espressif/openocd-esp32"
arch="aarch64"
license="GPL-2.0-or-later"
depends="libusb"
makedepends="git make autoconf libtool pkgconf libusb-dev automake zlib-dev"
checkdepends=""
install=""
subpackages=""
source="10-xtensa.patch"
builddir="$srcdir/$pkgname-$pkgver"

prepare() {
	git clone --depth 1 --branch "v$pkgver-esp32-20230419" https://github.com/espressif/openocd-esp32.git $builddir
    default_prepare
}

build() {
    ./bootstrap
    ./configure --enable-sysfsgpio --enable-bcm2835gpio --prefix=/usr
	make
}

check() {
	:
}

package() {
	install -Dm644 LICENSES/license-rules.txt "$pkgdir"/usr/share/licenses/$pkgname/license.txt
	make DESTDIR="$pkgdir" install
    # Remove man page
    rm -r $pkgdir/usr/share/man
}

sha512sums="
036a60e403f6f8d7dcf02997b542962e1ec315be4331af36af69aff727cf9f90eb8c343b69a81109427c25a345202dc351d2a56ff8879d9c8b5e80f918adca71  10-xtensa.patch
"
