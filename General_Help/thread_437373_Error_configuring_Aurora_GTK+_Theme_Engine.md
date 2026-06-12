---
title: "Error configuring Aurora GTK+ Theme Engine"
date: 2007-05-08
forum: General Help
---

### Post by zvoase on 2007-05-08
I am currently trying to compile the Aurora GTK+ engine on my ubuntu 7.04 i386 Desktop laptop. The problem is, every time I try to compile I receive an error; the pkg-config file for GTK has not been found. Of course, I have the latest version of GTK and so do not understand why this error keeps popping up, apart from the fact that there is no .pc file for GTK. The last few lines of ouput are here:
```
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... no
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for GTK... no
configure: error: GTK+-2.10 is required to compile aurora

```
Also, the output from the following command is shown below:
```
$ dpkg -s libgtk2.0-common 
Package: libgtk2.0-common
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 15612
Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
Architecture: all
Source: gtk+2.0
Version: 2.10.11-0ubuntu3
Replaces: libgtk1.3-common, libgtk2.0-data
Depends: libgtk2.0-0
Conflicts: libgtk1.3-common, libgtk2.0-data
Description: Common files for the GTK+ graphical user interface library
 The GTK+ is a multi-platform toolkit for creating graphical user
 interfaces. Offering a complete set of widgets, the GTK+ is suitable
 for projects ranging from small one-off tools to complete application
 suites.
 .
 This package contains the common files which the libraries need.
Original-Maintainer: Sebastien Bacher <seb128@debian.org>

```
If anyone could help as to how to solve this problem, or obtain the necessary binary or GTK pkg-config file, I would greatly appreciate it.

---

### Post by natbudin on 2007-05-11
apt-get install libgtk2.0-dev

---

### Post by dilomo on 2007-06-28
I'm having the same problem here. zvoase did you find solution yet?

---

### Post by dilomo on 2007-06-29
I find a solution - the problem was that I previously installed pkg-config and that I conflicts with another version on my pc so I had to uninstall it and everything worked fine

---

