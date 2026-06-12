---
title: "libgfortran error"
date: 2018-07-12
forum: General Help
---

### Post by mona11 on 2018-07-12
error while loading shared libraries: libgfortran.so.3: cannot open shared object file: No such file or directory

i get this error while running one of my programmes for calculations
i am getting this after i upgraded to ubuntu 18.04 LTS

it would be very helpful if i get some help on how to solve this

---

### Post by steeldriver on 2018-07-12
The libgfortran.so.3 library should be available via package [libgfortran3](https://packages.ubuntu.com/bionic/libgfortran3) on 18.04

It's already installed on my 18.04 system - however I think that's likely because I upgraded from a previous release that had pulled in libgfortran3 as a dependency of the gfortran-6 compiler - the default for 18.04 seems to be libgfortran4 which is probably why your program breaks

If it's a program that you have written and compiled yourself, you might want to simply re-build it with gfortran-7

---

