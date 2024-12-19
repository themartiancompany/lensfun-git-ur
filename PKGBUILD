# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>
# Maintainer: éclairevoyant
# Contributor: Hyacinthe Cartiaux <hyacinthe.cartiaux at free dot fr>
# Contributor: zhuqin <zhuqin83 at gmail dot com>

_os="$( \
  uname \
    -o)"
if [[ "${_os}" == "GNU/Linux" ]]; then
  _libc="glibc"
elif [[ "${_os}" == "Android" ]]; then
  _libc="ndk-sysroot"
fi
_py="python"
_pkg=lensfun
_pkgname="${_pkg}"
pkgname="$_pkgname-git"
pkgver=0.3.2.r2592.gec9412d2
pkgrel=1
pkgdesc='Database of photographic lenses and associated library'
arch=(
  'i686'
  'x86_64'
  'mips'
  'pentium'
  'arm'
  'aarch64'
  'armv7l'
  'armv6l'
  'pentium4'
)
url="https://${_pkg}.github.io/"
license=(
  'LGPL3'
)
depends=(
  "${_libc}"
  'glib2'
)
makedepends=(
  'cmake'
  'git'
  'libpng'
  "${_py}-setuptools"
)
optdepends=(
  "${_py}: for lensfun-update-data and lensfun-add-adapter"
)
provides=(
  "${_pkg}=0.3.4"
)
conflicts=(
  "${_pkgname}"
)
_http="https://github.com"
_ns="${_pkg}"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "git+${_url}.git"
)
b2sums=(
  'SKIP'
)

pkgver() {
  cd \
    "${_pkg}"
  git \
    describe \
      --long | \
    sed \
      -r \
      's/^v//;s/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd \
    "${_pkg}"
  cmake \
    -DCMAKE_INSTALL_PREFIX=/usr \
    -DCMAKE_INSTALL_LIBDIR=lib \
    -DCMAKE_BUILD_TYPE=Release \
    .
  make
}

package() {
  cd \
    "${_pkg}"
  make \
    DESTDIR="${pkgdir}" \
    install
}
