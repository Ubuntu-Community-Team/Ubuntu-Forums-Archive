---
title: "Can't install draftsite due to apparent package dependancy issue"
date: 2013-06-04
forum: General Help
---

### Post by kerryhall on 2013-06-04
This pretty much says it all:

```

kerry@kerry-desktop:~/Desktop$ sudo dpkg -i draftSight.deb 
dpkg: regarding draftSight.deb containing dassault-systemes-draftsight:i386, pre-dependency problem:
 dassault-systemes-draftsight:i386 pre-depends on libdirectfb-extra (>= 1.2.7-2)
dpkg: error processing draftSight.deb (--install):
 pre-dependency problem - not installing dassault-systemes-draftsight:i386
Errors were encountered while processing:
 draftSight.deb

```

```

kerry@kerry-desktop:~/Desktop$ sudo apt-get install libdirectfb-extra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libdirectfb-extra is already the newest version.
The following packages were automatically installed and are no longer required:
  libcurl3-gnutls:i386 libllvm3.0:i386
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

```

kerry@kerry-desktop:~/Desktop$ dpkg -s libdirectfb-extra
Package: libdirectfb-extra
Status: install ok installed
Priority: optional
Section: libs
Installed-Size: 137
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: directfb
Version: 1.2.10.0-4.3ubuntu1
Depends: libdirectfb-1.2-9 (= 1.2.10.0-4.3ubuntu1), libc6 (>= 2.11), libfreetype6 (>= 2.2.1), libjpeg8 (>= 8c), libpng12-0 (>= 1.2.13-4), libx11-6, libxext6
Description: direct frame buffer graphics - extra providers
 DirectFB is a graphics library which was designed with embedded systems
 in mind. It offers maximum hardware accelerated performance at a minimum
 of resource usage and overhead.
 .
 This package contains the following providers:
 .
   * image PNG
   * image JPEG
   * font FreeType
   * system X11
Homepage: http://www.directfb.org/
Original-Maintainer: Debian DirectFB Team <pkg-directfb-devel@lists.alioth.debian.org>

```

So yes, that package is installed, and yes it satisfies the version requirements. Now what? (My only guess is it's an architecture issue, but unsure how to proceed) 

Running Ubuntu 12.04.2 64 bit. Thanks!!

---

### Post by searchfgold6789 on 2013-06-06
Since you're trying to install the 32 bit version of a package, it will only call for the 32 bit versions of any libraries it requires (recall all the frustration people were having when 64 bit first came out). Since you only have the 64 bit version of libdirectfb, and the package requires the 32 bit version, you should either attempt to find a 64 bit version of draftSight.deb (probably easier), or replace all the 64 bit versions of the libraries it requires with 32 bit versions, which could easily cause a system messup. If you really need to use that 32 bit program, the easiest (but not always the most convenient) way to do that would be to install the 32 bit version of Ubuntu.

---

