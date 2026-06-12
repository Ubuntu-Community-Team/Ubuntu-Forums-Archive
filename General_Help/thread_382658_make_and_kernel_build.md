---
title: "make and kernel build"
date: 2007-03-12
forum: General Help
---

### Post by shiznatix on 2007-03-12
I am trying to install the latest version of ndiswrapper but whenever I download it and try to run make and make install i get this error:

> shiznatix@shiznatix-laptop:~/Desktop/ndiswrapper-1.38$ make
make -C driver
make[1]: Entering directory `/home/shiznatix/Desktop/ndiswrapper-1.38/driver'
Can't find kernel build files in /lib/modules/2.6.17-11-386/build;
  give the path to kernel build directory with 
  KBUILD=<path> argument to make
make[1]: *** [prereq_check] Error 1
make[1]: Leaving directory `/home/shiznatix/Desktop/ndiswrapper-1.38/driver'
make: *** [all] Error 2


I don't know how to give it my kernel build path but I think I shouldnt have to do that every time I try to install something this way. How can I fix this?

---

### Post by solar george on 2007-03-13
Install the kernel headers package.

---

