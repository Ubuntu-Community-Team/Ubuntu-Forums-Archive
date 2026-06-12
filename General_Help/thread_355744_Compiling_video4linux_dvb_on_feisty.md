---
title: "Compiling video4linux dvb on feisty"
date: 2007-02-07
forum: General Help
---

### Post by beniwtv on 2007-02-07
Hi,

I'm trying to install video4linux dvb for my new dvb card...

But I get this error:

creating symbolic links...
make -C /lib/modules/2.6.20-6-generic/build SUBDIRS=/home/beni/Desktop/driver/v4l-dvb/v4l  modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-6-generic'
  CC [M]  /home/beni/Desktop/driver/v4l-dvb/v4l/v4l1-compat.o
/home/beni/Desktop/driver/v4l-dvb/v4l/v4l1-compat.c:20:26: error: linux/config.h: No such file or directory
make[2]: *** [/home/beni/Desktop/driver/v4l-dvb/v4l/v4l1-compat.o] Error 1
make[1]: *** [_module_/home/beni/Desktop/driver/v4l-dvb/v4l] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-6-generic'
make: *** [default] Error 2

I have installed the kernel headers and linux-source already...

Can someone help me?

Thanks.

---

