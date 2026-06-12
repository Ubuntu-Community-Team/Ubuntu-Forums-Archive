---
title: "Box Backup on Ubuntu 6.10"
date: 2006-12-28
forum: General Help
---

### Post by nattugglan on 2006-12-28
Hi.

Does anyone have a step-by-step guide to compile and install Box Backup ([http://www.fluffy.co.uk/boxbackup/](http://www.fluffy.co.uk/boxbackup/)) from source
on Ubuntu 6.10?
I'm stuck on ./configure.. ](*,) 

./configure gives the following in config.log:
> ## ----------- ##
## Core tests. ##
## ----------- ##

configure:1401: checking build system type
configure:1419: result: powerpc-unknown-linux-gnu
configure:1427: checking host system type
configure:1441: result: powerpc-unknown-linux-gnu
configure:1449: checking target system type
configure:1463: result: powerpc-unknown-linux-gnu
configure:1539: checking for g++
configure:1568: result: no
configure:1539: checking for c++
configure:1568: result: no
configure:1539: checking for gpp
configure:1568: result: no
configure:1539: checking for aCC
configure:1568: result: no
configure:1539: checking for CC
configure:1568: result: no
configure:1539: checking for cxx
configure:1568: result: no
configure:1539: checking for cc++
configure:1568: result: no
configure:1539: checking for cl
configure:1568: result: no
configure:1539: checking for FCC
configure:1568: result: no
configure:1539: checking for KCC
configure:1568: result: no
configure:1539: checking for RCC
configure:1568: result: no
configure:1539: checking for xlC_r
configure:1568: result: no
configure:1539: checking for xlC
configure:1568: result: no
configure:1581: checking for C++ compiler version
configure:1584: g++ --version </dev/null >&5
./configure: line 1585: g++: command not found
configure:1587: $? = 127
configure:1589: g++ -v </dev/null >&5
./configure: line 1590: g++: command not found
configure:1592: $? = 127
configure:1594: g++ -V </dev/null >&5
./configure: line 1595: g++: command not found
configure:1597: $? = 127
configure:1620: checking for C++ compiler default output file name
configure:1623: g++    conftest.cc  >&5
./configure: line 1624: g++: command not found
configure:1626: $? = 127
configure: failed program was:
| /* confdefs.h.  */
| 
| #define PACKAGE_NAME "Box Backup"
| #define PACKAGE_TARNAME "box-backup"
| #define PACKAGE_VERSION "0.09"
| #define PACKAGE_STRING "Box Backup 0.09"
| #define PACKAGE_BUGREPORT "box@fluffy.co.uk"
| /* end confdefs.h.  */
| 
| int
| main ()
| {
| 
|   ;
|   return 0;
| }
configure:1665: error: C++ compiler cannot create executables

:. Regards,
   nattugglan

   Mac mini G4

---

### Post by rbalfour on 2006-12-28
You're missing the dev tools.

$ apt-get install build-essential


I downloaded the source and it configs and compiles fine.

---

### Post by nattugglan on 2006-12-28
> **rbalfour said:**
> $ apt-get install build-essential

Thank you. :-D 

It compiled fine, and all tests passed.

---

