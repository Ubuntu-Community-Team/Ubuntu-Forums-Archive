---
title: "need help with two programs..."
date: 2006-10-02
forum: General Help
---

### Post by pentium on 2006-10-02
I just downloaded google earth for ubuntu and to my delight it is running in open gl mode which is very slow. It tells me that I have an unknown video card and to update the driver. I have a 32 mb leadtek AGP card with a GeForce 2 GTS/PRO chipset. I can't find a driver for ir and one attempt at uodating the driver actually caused GDM to be disabled. Where could I find an appropriate driver and do I also need something directX-like to get smoother operation?

second...
I found a linux version copy of File System Navigator (FSN) called FSV. The problem is that it looks like I either have to manually set it up or it isn't compatible with ubuntu, period. How can I get this program running?

---

### Post by pentium on 2006-10-03
did I post in the wrong forum or something?

---

### Post by slimdog360 on 2006-10-03
Im guessing your video card is a Nvidia card? If it is tery the legacy driver from synaptic.

for the other question, 'manually set it up', do you mean you have to compile it from source? If you do just un-tar the file into a new folder then open a terminal and cd to the folder. Then use the following code one line at a time.
```
./config
make 
makeinstall
```
it could also be ./configure rather then ./config so if the first one doesnt work try the other.

---

### Post by pentium on 2006-10-03
okay, I am still new to the world of linux.
what do you mean one line at a time?
here is the folders and files:
```
debug
doc
intl
lib
po
src
ABOUT-NLS
acconfig.h
aclocal.m4
AUTHORS
ChangeLog
config.h.in
configure
configure.in
COPYING
fsv.spec
fsv.spec.in
fsv.wmconfig
INSTALL <---------EMPTY SCRIPT!
install-sh
Makefile.am
Makefile.in
missing
mkinstalldirs
NEWS
NOTES
README
stamp-h.in
TODO

```
is there something here that will shed some light.
also,> tery the legacy driver from synaptic.
 What does that mean?

---

### Post by slimdog360 on 2006-10-03
I meant the Nvidia legacy driver. Search for Nvidia. First you may have to enable the extra repositories.

By one line at a time I mean, type in 
```
sudo ./configure
```
then wait till its finished
```
make
```
again wait
```
sudo make install
```

Im not to sure if you need the sudo out the front of the ./configure though? but it should work either way.

---

### Post by pentium on 2006-10-03
I fixed the driver.

as for sudo ./configure

```
checking for a BSD compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking whether make sets ${MAKE}... no
checking for working aclocal... missing
checking for working autoconf... missing
checking for working automake... missing
checking for working autoheader... missing
checking for working makeinfo... missing
checking for gcc... no
checking for cc... no
configure: error: no acceptable cc found in $PATH

```

---

### Post by slimdog360 on 2006-10-03
sudo apt-get install build-essential

---

### Post by Jussi Kukkonen on 2006-10-03
> **slimdog360 said:**
> Im not to sure if you need the sudo out the front of the ./configure though? but it should work either way.

No, you don't need it. configure and make should only modify files inside the build directory.

If you get the source with "apt-get source", I suggest not using the *"configure && make && sudo make install"* though, but instead running this in the source directory:
```
dpkg-buildpackage -rfakeroot -uc -us
```
That creates a deb-package in the directory above the source dir. You can install it with *dpkg -i <package.deb>*, and then you have it in the normal package handling system -- no rogue files on your system...

---

### Post by pentium on 2006-10-03
suod ./configure now gives this after a long list:
```
checking for GTK - version >= 1.2.1... no
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: Cannot find proper GTK+ version

```
I also tried dpkg-buildpackage -rfakeroot -uc -us  and got this:
```
dpkg-parsechangelog: error: cannot open debian/changelog to find format: No such file or directory
dpkg-buildpackage: unable to determine source package is

```

---

### Post by pentium on 2006-10-03
Anyone gonna help?
FSV is wasting space just sitting on my drive.

---

### Post by pentium on 2006-10-03
**moved**
since this is no longer a hrdwareproblem and now just a software problem, This will be moved to "Other Support Options" forum.
thanks for the driver update.

---

