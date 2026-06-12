---
title: "gfortran package in ubuntu 8.04"
date: 2008-06-15
forum: General Help
---

### Post by richardmems on 2008-06-15
Dear all

Please kindly let me know if gfortran package is there in original ubuntu 8.04 installation.

when i type gfortran, console replied gfortran not install and ask to type

apt-get install gfortran

but when i type this command, i got the error "couldn't find gfortran package"

is my system missing gfortran package or link to gfortran package that sys cannot find it. and How to get gfortran install on my computer?

thanks 
Richard

---

### Post by ad_267 on 2008-06-15
```
apt-cache search gfortran
```
```
gfortran-4.2 - The GNU Fortran 95 compiler
gfortran-4.2-doc - Documentation for the GNU Fortran compiler (gfortran)
lib64gfortran2 - Runtime library for GNU Fortran applications (64bit)
lib64gfortran2-dbg - Runtime library for GNU Fortran applications (64bit debug symbols)
libgfortran2 - Runtime library for GNU Fortran applications
libgfortran2-dbg - Runtime library for GNU Fortran applications (debug symbols)
gfortran-4.1 - The GNU Fortran 95 compiler
gfortran-4.1-doc - Documentation for the GNU Fortran compiler (gfortran)
gfortran-4.1-multilib - The GNU Fortran 95 compiler (multilib files)
gfortran-4.2-multilib - The GNU Fortran 95 compiler (multilib files)
lib64gfortran1 - Runtime library for GNU Fortran applications (64bit)
libcojets2-gfortran - [Physics] COJETS p-p and pbar-p interaction Monte Carlo library
libeurodec1-gfortran - [Physics] Monte Carlo library for quark and heavy lepton decays
libgeant321-2-gfortran - [Physics] Library for GEANT 3.21
libgfortran1 - Runtime library for GNU Fortran applications
libgraflib1-gfortran - CERNLIB data analysis suite - graphical library
libgrafx11-1-gfortran - CERNLIB data analysis suite - interface to X11 and PostScript
libherwig59-2-gfortran - [Physics] Monte Carlo event generator simulating hadronic events
libisajet758-3-gfortran - [Physics] Monte Carlo generator for proton / electron reactions
libkernlib1-gfortran - CERNLIB data analysis suite - core library of basic functions
libmathlib2-gfortran - CERNLIB data analysis suite - core mathematical library
libpacklib-lesstif1-gfortran - CERNLIB data analysis suite - core GUI library
libpacklib1-gfortran - CERNLIB data analysis suite - core library
libpawlib-lesstif3-gfortran - CERNLIB PAW library (Lesstif-dependent part)
libpawlib2-gfortran - CERNLIB PAW library - portion without Lesstif dependencies
libpdflib804-2-gfortran - [Physics] Comprehensive library of parton density functions
libphotos202-1-gfortran - [Physics] Monte Carlo simulation of photon radiation in decays
libphtools2-gfortran - [Physics] General purpose Monte Carlo routines
ppu-gfortran - PPU Fortran compiler
spu-gfortran - SPU cross-compiler (Fortran compiler)
gfortran - The GNU Fortran 95 compiler
gfortran-doc - Documentation for the GNU Fortran compiler (gfortran)
gfortran-multilib - The GNU Fortran 95 compiler (multilib files)
```

It's there for me with 8.04. What architecture are you using? It's available for i386 and amd64.

---

### Post by sparkyy on 2008-09-05
Same problem as above.

apt-cache search gfortran

generates references to gfortran douments (which I installed using synaptic) but nothing else.

My install is amd64 and the DVD was included in [www.Linux-Magazine.com](www.Linux-Magazine.com) magazine special Ubuntu edition issue 01/2008

Please someone help with this it is frustrating me no end.

cheers

---

### Post by ad_267 on 2008-09-05
Do you have the Universe repositories enabled under System - Administration - Software Sources? Or from the repositories options in Synaptic.

Although if you have Ubuntu 7.10 then you shouldn't need that.
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gfortran](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=gfortran)

---

