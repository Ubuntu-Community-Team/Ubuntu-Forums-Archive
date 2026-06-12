---
title: "dpkg-buildpackage problem"
date: 2008-05-09
forum: General Help
---

### Post by emmeelle on 2008-05-09
Hi!

I'm trying generate package .deb from sources, I'm following this guide:

[http://www.debian.org/doc/manuals/reference/ch-package.it.html](http://www.debian.org/doc/manuals/reference/ch-package.it.html)

My problem is that dpkg-buildpackage doesn't create the package .deb, so when I try installing it, I have an error because it doesn't find the package.

```

$ dpkg-source -x pomm*.dsc
gpg: Signature made sab 09 feb 2008 09:24:01 CET using DSA key ID F5D65169
gpg: Can't check signature: public key not found
dpkg-source: extracting pommed in pommed-1.15~dfsg
dpkg-source: unpacking pommed_1.15~dfsg.orig.tar.gz
dpkg-source: applying ./pommed_1.15~dfsg-1.diff.gz

$ cd pomm*


~/Scrivania/pommed-1.15~dfsg$ sudo dpkg-buildpackage -rfakeroot -us -uc
[sudo] password for manuela: 
dpkg-buildpackage: warning: using a gain-root-command while being root
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: source package pommed
dpkg-buildpackage: source version 1.15~dfsg-1
dpkg-buildpackage: source changed by Julien BLACHE <jblache@debian.org>
dpkg-buildpackage: host architecture i386
dpkg-checkbuilddeps: Unmet build dependencies: pciutils-dev libsmbios-dev (>= 0.13.5-1) libconfuse-dev libasound2-dev libaudiofile-dev libglade2-dev libgtk2.0-dev libdbus-1-dev libxext-dev libxpm-dev
dpkg-buildpackage: warning: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: warning: (Use -d flag to override.)


~dfsg$ su -c "dpkg -i pomm*.deb"Password: 
dpkg: errore processando pomm*.deb (--install):
 impossibile accedere all'archivio: No such file or directory
Sono occorsi degli errori processando:
 pomm*.deb


```

Thanks.

---

### Post by sdennie on 2008-05-09
It looks like you may need to run:

```

sudo apt-get build-dep pommed

```

Before you try to build the package.

---

