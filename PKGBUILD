# Maintainer: Patrick Ulbrich <zulu99 at gmx . net>
# Contributor: rasmus <rasmus . pank at gmail . com>

pkgname=mailnag
pkgver=0.5.2
pkgrel=3
pkgdesc="A mail notification daemon for GNOME 3."
arch=('any')
url="https://github.com/pulb/mailnag"
license=('GPL')
depends=('python2' 'python2-gobject' 'python2-httplib2'
        'libgnome-keyring' 'gnome-keyring' 'python2-xdg'
        'python2-dbus' 'libnotify' 'gstreamer0.10-base-plugins')
makedepends=('gettext')
source=('https://launchpad.net/mailnag/trunk/mailnag-master/+download/mailnag-0.5.2.tar.gz')
md5sums=('10bb4d1618dce791f7ae619f81580a68')
install='mailnag.install'

build() {
  # python2 fix
  cd "${srcdir}"
  sed -i 's/python/python2/g' mailnag
  sed -i 's/python/python2/g' mailnag_config
  find -name "*.py" -exec sed -i 's_#!.*/usr/bin/env.*python_#!/usr/bin/env python2_' {} \;
}

package() {
  cd "${srcdir}"
  python2 setup.py install --root=${pkgdir}
  install -D -m644 LICENSE "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}