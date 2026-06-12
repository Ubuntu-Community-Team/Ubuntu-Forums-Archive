---
title: "Problem installing app from source."
date: 2005-05-03
forum: General Help
---

### Post by void_false on 2005-05-03
Hi all! 
I´m trying to install Free Disk Space Applet from [KDE-APPS](http://www.kde-apps.org/content/show.php?content=23396&PHPSESSID=e37ab740ec3a56020ccf65ff8e63d876)
I open folder and type in console ./configure. Here´s output:
```

sh ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

``` 
It says I have no GCC. But when I check synaptik I have gcc-3.3-base installed. So what´s the problem?

---

### Post by syltty on 2005-05-03
auto-apt is a great tool when compiling from sources

try if this helps:
$ sudo apt-get install auto-apt
$ sudo auto-apt update
$ sudo auto-apt updatedb
$ sudo auto-apt update-local
$ auto-apt run ./configure
$ ./configure

---

### Post by void_false on 2005-05-03
Nope. Didnt help. Same error.

BTW why cant I just use su instead of typing sudo everytime?

---

### Post by cutOff on 2005-05-03
```
$ sudo apt-get install build-essential
``` 
And try again.

---

### Post by void_false on 2005-05-04
THX it helped in some way. But now i got new error:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
``` 
WTF?  :???:

---

### Post by void_false on 2005-05-05
Anyone? Please.  :-?

---

### Post by shakin on 2005-05-05
[QUOTE=void_false]THX it helped in some way. But now i got new error:
```
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!
``` 
WTF?  :???:[/QUOTE]

There is probably an Xorg-devel package you need to get.

---

### Post by void_false on 2005-05-06
[QUOTE=shakin]There is probably an Xorg-devel package you need to get.[/QUOTE]
I´ve searched Synaptic and didnt find any Xorg-devel packages.  :neutral:

---

### Post by az on 2005-05-06
Any binary package against which you want to compile stuff requires that you have the developmental headers.

Look for xlibs-dev or kdelibs-dev or any other lib your configure script cannot find...

---

### Post by void_false on 2005-05-07
Thx everybody for input. After I´ve installed aditional 100mo of dependencies for this baby I finally decided to remove it.  :mrgreen: 
While removing those packages I almost trashed my KDE.

Anyway does anyone know good applet for systray to show info on disks?

---

