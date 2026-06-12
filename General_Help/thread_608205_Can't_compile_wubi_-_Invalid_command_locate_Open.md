---
title: "Can't compile wubi - Invalid command: locate::_Open"
date: 2007-11-09
forum: General Help
---

### Post by mantiena on 2007-11-09
Hi,

you told me, that adding new distro support to wubi is very simpe - just add distro to isolist.ini and do
make prerequisites
and
make cdboot

But I get an error when I run make cdboot - see output from terminal:
[..]
FileWrite: DetectIso->$logfilehandle
FileWrite: 
->$logfilehandle
FileClose: $logfilehandle
!insertmacro: _EndIf
!insertmacro: end of _EndIf
!insertmacro: end of log
!insertmacro: end of debug
!insertmacro: locate::Open
Invalid command: locate::_Open
Error in macro locate::Open on macroline 1
!include: error in script: "inspector\detect_iso.nsh" on line 16
!include: error in script: "inspector\inspector.nsh" on line 3
Error in script "wubi/wubi.nsi" on line 17 -- aborting creation process
mv: cannot stat `wubi/*.exe': No such file or directory
make: *** [all] Error 1

Please, tell me why this error happens or compile wubi and wubi-cdboot with Baltix Linux suppport (ubuntu-based distro, look at [http://wiki.ubuntu.com/Baltix](http://wiki.ubuntu.com/Baltix) and [http://ubuntu.com/products/whatisubuntu/derivatives](http://ubuntu.com/products/whatisubuntu/derivatives) for more info, latest ISO image (ver 3.0) is available from [ftp://ftp.akl.lt/Linux/Baltix/](ftp://ftp.akl.lt/Linux/Baltix/) )

---

### Post by ago on 2007-11-09
make all
make cdboot

---

### Post by mantiena on 2007-11-09
Hehe, it seems wubi compilation is successful if I do "make all" firstly ;)
One strange think is, that "make all" produces different revision of Wubi-7.10-alpha.exe, than simple make or make cdboot :-/
When I did "make all" I got Wubi-7.10-alpha-rev384.exe in dist folder, but after make or "make cdboot" I get rev385 :-/

---

### Post by molk on 2007-11-10
Ago,

I tried compiling also. I like the way you have the prerequisites scripts downloading and installing all of the necessary software to build Wubi. 

One thing I noticed is that this does not happen for the mono-mcs package which is required to build Wubibcd. It might be a good idea to add a makefile to the /plugins.src/wubibcd directory which would install mono-mcs if it is not there. I tried building Wubi on Ubuntu 7.10 and mono-mcs was not on the system by default which caused build errors.

---

### Post by ago on 2007-11-11
> **molk said:**
> Ago,

I tried compiling also. I like the way you have the prerequisites scripts downloading and installing all of the necessary software to build Wubi. 

One thing I noticed is that this does not happen for the mono-mcs package which is required to build Wubibcd. It might be a good idea to add a makefile to the /plugins.src/wubibcd directory which would install mono-mcs if it is not there. I tried building Wubi on Ubuntu 7.10 and mono-mcs was not on the system by default which caused build errors.
will be in next build

---

