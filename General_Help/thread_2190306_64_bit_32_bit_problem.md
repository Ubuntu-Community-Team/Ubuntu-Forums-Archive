---
title: "64 bit 32 bit problem"
date: 2013-11-26
forum: General Help
---

### Post by profgeorgefhart on 2013-11-26
Any help on this one?  I may need another group but it is worth a try as I have spent 6 hours on the problem so far.

 

 I recently upgraded to 64 bit Ubuntu 13.10 for a new 64 bit motherboard.  I use the R statistical package constantly but find some pgms will not install.   It seems that I have the 32 bit  rather than the 64 bit FORTRAN compiler.  Could this be the problem?  How do I update the Fortran compiler?
 The basic error seems to be: wrong ELF class: ELFCLASS32
 
Here is the output.

George Hart

…...........................................................................................
 R version 3.0.2 (2013-09-25) -- "Frisbee Sailing" 
 Copyright (C) 2013 The R Foundation for Statistical Computing 

 Platform: x86_64-pc-linux-gnu (64-bit) 

  
   > library(ggplot2) 
 Error in dyn.load(file, DLLpath = DLLpath, ...) :  
   unable to load shared object '/usr/lib/R/mylibrary/digest/libs/digest.so': 
   /usr/lib/R/mylibrary/digest/libs/digest.so: wrong ELF class: ELFCLASS32 
 

 …........................................................................................................................................................
    
> library(ggplot2) 
 Error in dyn.load(file, DLLpath = DLLpath, ...) :  
   unable to load shared object '/usr/lib/R/mylibrary/digest/libs/digest.so': 
   /usr/lib/R/mylibrary/digest/libs/digest.so: wrong ELF class: ELFCLASS32 

 
 

 > sessionInfo() 

 R version 3.0.2 (2013-09-25) 
 Platform: x86_64-pc-linux-gnu (64-bit) 
  
 locale: 
  [1] LC_CTYPE=en_US.UTF-8       LC_NUMERIC=C               LC_TIME=en_US.UTF-8        LC_COLLATE=en_US.UTF-8     LC_MONETARY=en_US.UTF-8    
  [6] LC_MESSAGES=en_US.UTF-8    LC_PAPER=en_US.UTF-8       LC_NAME=C                  LC_ADDRESS=C               LC_TELEPHONE=C             
 [11] LC_MEASUREMENT=en_US.UTF-8 LC_IDENTIFICATION=C        
  
 attached base packages: 
 [1] stats     graphics  grDevices utils     datasets  methods   base

---

### Post by Bashing-om on 2013-11-26
profgeorgefhart; Hi !

I may be stepping into things I know little or nothing about; but, is this worth considering ?
```

sysop@1304mini:~$ apt-cache show gfortran-4.7-multili
Package: gfortran-4.7-multilib
Priority: optional
Section: devel
Installed-Size: 21
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: amd64
Source: gcc-4.7
Version: 4.7.3-1ubuntu1
Depends: gcc-4.7-base (= 4.7.3-1ubuntu1), gfortran-4.7 (= 4.7.3-1ubuntu1), gcc-4.7-multilib (= 4.7.3-1ubuntu1), lib32gfortran-4.7-dev (= 4.7.3-1ubuntu1), libx32gfortran-4.7-dev (= 4.7.3-1ubuntu1)
Filename: pool/main/g/gcc-4.7/gfortran-4.7-multilib_4.7.3-1ubuntu1_amd64.deb
Size: 922
MD5sum: a7ec6e8232ed83316af9fdcab63dd6c2
SHA1: a310ad563ccd0f1067731d50f5586b543275f410
SHA256: d724d4043407c0e7c3cce1f91345becb8ebc80694319c9e12cbce0c3f45eec2b
Description-en: GNU Fortran compiler (multilib files)
 This is the GNU Fortran compiler, which compiles Fortran on platforms
 supported by the gcc compiler.
 .
 On architectures with multilib support, the package contains files
 and dependencies for the non-default multilib architecture(s).
Homepage: http://gcc.gnu.org/
Description-md5: 005da023d3d2e21ed1c3e72be2361917
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 9m

Package: gfortran-4.7-multilib-arm-linux-gnueabi
Priority: extra
Section: universe/devel
Installed-Size: 21
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: amd64
Source: gcc-4.7-armel-cross (1.81)
Version: 4.7.3-1ubuntu1cross1.81
Depends: gcc-4.7-arm-linux-gnueabi-base (= 4.7.3-1ubuntu1cross1.81), gfortran-4.7-arm-linux-gnueabi (= 4.7.3-1ubuntu1cross1.81), gcc-4.7-multilib-arm-linux-gnueabi (= 4.7.3-1ubuntu1cross1.81), libhfgfortran-4.7-dev-armel-cross (= 4.7.3-1ubuntu1cross1.81) | libhfgfortran-4.7-dev-armel-cross
Filename: pool/universe/g/gcc-4.7-armel-cross/gfortran-4.7-multilib-arm-linux-gnueabi_4.7.3-1ubuntu1cross1.81_amd64.deb
Size: 1014
MD5sum: beb25c652f679b7600a06b5281f31607
SHA1: 52e4ec9fee82cf30e129b1129abb308fe563403b
SHA256: bce772871dea81ab32de6a37918a8c9cebac999adcaf4da49bac79c315b70af3
Description-en: GNU Fortran compiler (multilib files)
 This is the GNU Fortran compiler, which compiles Fortran on platforms
 supported by the gcc compiler.
 .
 On architectures with multilib support, the package contains files
 and dependencies for the non-default multilib architecture(s).
Built-Using: gcc-4.7 (= 4.7.3-1ubuntu1cross1.81)
Homepage: http://gcc.gnu.org/
Description-md5: 005da023d3d2e21ed1c3e72be2361917
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: gfortran-4.7-multilib-arm-linux-gnueabihf
Priority: extra
Section: universe/devel
Installed-Size: 21
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: amd64
Source: gcc-4.7-armhf-cross (1.81)
Version: 4.7.3-1ubuntu1cross1.81
Depends: gcc-4.7-arm-linux-gnueabihf-base (= 4.7.3-1ubuntu1cross1.81), gfortran-4.7-arm-linux-gnueabihf (= 4.7.3-1ubuntu1cross1.81), gcc-4.7-multilib-arm-linux-gnueabihf (= 4.7.3-1ubuntu1cross1.81), libsfgfortran-4.7-dev-armhf-cross (= 4.7.3-1ubuntu1cross1.81) | libsfgfortran-4.7-dev-armhf-cross
Filename: pool/universe/g/gcc-4.7-armhf-cross/gfortran-4.7-multilib-arm-linux-gnueabihf_4.7.3-1ubuntu1cross1.81_amd64.deb
Size: 1018
MD5sum: 7d67cad96f7b4087d233c458b21e49ed
SHA1: 373c1c5dbc30e8d7d5f290c9cdbcbb48866a3c37
SHA256: 38fca15e884eba2b413b2df60ae5d4a2e28837bb83d9cbacb51e0a401ad7b150
Description-en: GNU Fortran compiler (multilib files)
 This is the GNU Fortran compiler, which compiles Fortran on platforms
 supported by the gcc compiler.
 .
 On architectures with multilib support, the package contains files
 and dependencies for the non-default multilib architecture(s).
Built-Using: gcc-4.7 (= 4.7.3-1ubuntu1cross1.81)
Homepage: http://gcc.gnu.org/
Description-md5: 005da023d3d2e21ed1c3e72be2361917
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

Package: gfortran-4.7-multilib-powerpc-linux-gnu
Priority: extra
Section: universe/devel
Installed-Size: 21
Maintainer: Ubuntu Core developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian GCC Maintainers <debian-gcc@lists.debian.org>
Architecture: amd64
Source: gcc-4.7-powerpc-cross (0.7)
Version: 4.7.3-1ubuntu1cross0.7
Depends: gcc-4.7-powerpc-linux-gnu-base (= 4.7.3-1ubuntu1cross0.7), gfortran-4.7-powerpc-linux-gnu (= 4.7.3-1ubuntu1cross0.7), gcc-4.7-multilib-powerpc-linux-gnu (= 4.7.3-1ubuntu1cross0.7), lib64gfortran-4.7-dev-powerpc-cross (= 4.7.3-1ubuntu1cross0.7)
Filename: pool/universe/g/gcc-4.7-powerpc-cross/gfortran-4.7-multilib-powerpc-linux-gnu_4.7.3-1ubuntu1cross0.7_amd64.deb
Size: 1010
MD5sum: 4023989a7dd0321d7ce074c82806f1d5
SHA1: 56f1aaa2fe7f7ed48c6b77f8efa1c53b18fb8e35
SHA256: 3de913c47fdf84c4ff384b9323400292af25b2408d9850f6309c11ac65de657c
Description-en: GNU Fortran compiler (multilib files)
 This is the GNU Fortran compiler, which compiles Fortran on platforms
 supported by the gcc compiler.
 .
 On architectures with multilib support, the package contains files
 and dependencies for the non-default multilib architecture(s).
Built-Using: gcc-4.7 (= 4.7.3-1ubuntu1cross0.7)
Homepage: http://gcc.gnu.org/
Description-md5: 005da023d3d2e21ed1c3e72be2361917
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu

sysop@1304mini:~$ 

```

Just a thought to install different compiler(s) ?

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by profgeorgefhart on 2013-12-12
Thanks Bashing-om - I installed/updated the correct FORTRAN compiler - however that was not the problem with ggplot2 installation. I had to install 'scales' first, I had used dependencies =TRUE but it needed a direct install.packages("scales") before I could install ggplot2.

Seems to work now.

Regards,

gfh

---

### Post by Bashing-om on 2013-12-12
profgeorgefhart; Good Deal !

Glad ya got it fingered out.
As all is ship shape now, please mark this thread solved; 1st post ->thread tools.

[INDENT][INDENT]read ya next time 
[/INDENT][/INDENT]

---

