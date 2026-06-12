---
title: "installing driver help"
date: 2008-05-27
forum: General Help
---

### Post by hwang251 on 2008-05-27
I'm getting some error message when I run the command make to install a driver. The error is:

make -C /lib/modules/2.6.24-16-generic/build M=/home/dukerobotics/Documents/pcmmio modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/dukerobotics/Documents/pcmmio/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/dukerobotics/Documents/pcmmio] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2

---

