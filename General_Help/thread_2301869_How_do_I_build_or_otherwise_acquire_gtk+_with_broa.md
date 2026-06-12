---
title: "How do I build or otherwise acquire gtk+ with broadway support?"
date: 2015-11-05
forum: General Help
---

### Post by d-j-kasak-dk on 2015-11-05
Hi all. I'm a long-time Gentoo user, and attempting to get an application running on a Ubuntu VM ( 14.04 LTS ) for work. I'm using gtk's broadway backend, which in Gentoo can be enabled by setting the 'broadway' USE flag. It's proving to be quite difficult with Ubuntu, unfortunately.

First, I tried using the binaries from: [https://launchpad.net/~malizor/+archive/ubuntu/gtk-broadway](https://launchpad.net/~malizor/+archive/ubuntu/gtk-broadway). This package doesn't install cleanly. I get strange errors about incompatibilities, and I end up with a broadwayd binary, but with gtk+ build ***without*** broadway support.

Next I followed instructions at: [http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/](http://www.cyberciti.biz/faq/rebuilding-ubuntu-debian-linux-binary-package/). I edited debian/rules in the gtk+ source folder, and added --enable-broadway-backend. I then continued to build as per the instructions ( ie fakeroot debian/rules binary ). This ***almost*** works. It dies right at the end:

```
dh_install -plibgtk-3-0  --sourcedir=debian/install/shared
dh_link -plibgtk-3-0
dh_installmime -plibgtk-3-0
dh_installgsettings -plibgtk-3-0
dh_gconf -plibgtk-3-0
dh_icons -plibgtk-3-0
dh_translations -plibgtk-3-0
dh_langpack: processing files to add translation domain 'gtk30'..
# Install the binaries with a -3.0 suffix
mv debian/libgtk-3-0/usr/lib/x86_64-linux-gnu/libgtk-3-0/gtk-update-icon-cache \
        debian/libgtk-3-0/usr/lib/x86_64-linux-gnu/libgtk-3-0/gtk-update-icon-cache-3.0
mv: cannot stat ‘debian/libgtk-3-0/usr/lib/x86_64-linux-gnu/libgtk-3-0/gtk-update-icon-cache’: No such file or directory
make: *** [binary-install/libgtk-3-0] Error 1
root@ggs010:~/gtk+3.0-3.10.8#
```

I have no idea why this error occurs.

Does anyone know how I can get broadway support in gtk+ in Ubuntu 14.04?

---

