---
title: "Help with re-packaging a deb package"
date: 2007-06-15
forum: General Help
---

### Post by disturbedite on 2007-06-15
here is my problem:
i extracted the contents of a deb file so i could manually edit the control file to change a dependency.  that is the only change i made.  now how do i repackage the contents as a deb package?

---

### Post by az on 2007-06-15
> **disturbedite said:**
> here is my problem:
i extracted the contents of a deb file so i could manually edit the control file to change a dependency.  that is the only change i made.  now how do i repackage the contents as a deb package?

I am almost certain you don't want to do that.  If you really really do, use equivs instead.

apt-cache show equivs
Package: equivs
Priority: extra
Section: universe/admin
Installed-Size: 128
Maintainer: Peter Samuelson <peter@p12n.org>
Architecture: all
Version: 2.0.7
Depends: perl, debhelper (>= 4), dpkg-dev, devscripts, make, fakeroot
Filename: pool/universe/e/equivs/equivs_2.0.7_all.deb
Size: 18482
MD5sum: 89eba2fef58d3f3079f90e7578361e44
SHA1: 7a14011975e9b9c0fbbde8fec98910599061df3f
SHA256: 2520629f864e5f16739dd00321e99bef53e8276325f4d9952d3a6c22a0c47140
Description: Circumvent Debian package dependencies
 This package provides a tool to create Debian packages that only
 contain dependency information.
 .
 One use for this is to create a metapackage: a package whose sole
 purpose is to declare dependencies and conflicts on other packages so
 that these will be automatically installed, upgraded, or removed.
 .
 Another use is to circumvent dependency checking.  If a package P is
 not installed on the system, packages that depend on P cannot normally
 be installed.  However, if functionality equivalent to P is known to
 be installed, this tool can be used to trick the Debian package
 management system into believing that package P is actually installed.
 NOTE: this should be considered a crude hack to work around awkward
 situations, not a normal solution.  If you use equivs to work around
 bugs in other Debian packages, you should also file bug reports
 against those packages.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by disturbedite on 2007-06-16
that sounds very interesting, i will definitely try it.  thanks az.

nice avatar btw...i like rav tux's too.

---

### Post by nicksanders on 2007-06-19
Hi,

I was trying to do exactly the same thing. Equivs didn't work for me.

I found the webpage below that helped a lot and managed to work out a way to do it.

[http://synthesize.us/HOWTO_make_a_deb_archive_without_dpkg](http://synthesize.us/HOWTO_make_a_deb_archive_without_dpkg)

Here is how I did it

dpkg -e diskfree_0.15-1_i386.deb
cd DEBIAN/
nano control
tar -czvf control.tar.gz *
mv control.tar.gz ..
ar r diskfree_0.15-1_i386.deb control.tar.gz

I hope this helps

Regards

Nick

---

### Post by vulpes210 on 2008-02-16
Thanx Nick that did work for me.

Lucky you explained  how it's done because the link is dead

---

