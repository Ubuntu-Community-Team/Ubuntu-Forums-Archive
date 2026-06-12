---
title: "Installing driver for GadgetGeek usb hdtv"
date: 2013-08-14
forum: General Help
---

### Post by charlie_b on 2013-08-14
Hi,
I'm using Ubuntu 12.04 and I've just bought a GadgetGeek usb hdtv stick. It comes with a linux driver, but I'm having trouble installing it. Here is the readout from make:

st@myDesktop:~/Desktop/system/hdtv/IT9135_SRC$ sudo make
make -C /lib/modules/3.2.0-51-generic-pae/build SUBDIRS=/home/st/Desktop/system/hdtv/IT9135_SRC modules
make[1]: Entering directory `/usr/src/linux-headers-3.2.0-51-generic-pae'
  CC [M]  /home/st/Desktop/system/hdtv/IT9135_SRC/it9135-core.o
In file included from /home/st/Desktop/system/hdtv/IT9135_SRC/it9135-core.c:1:0:
/home/st/Desktop/system/hdtv/IT9135_SRC/it9135.h:15:21: fatal error: dvb-usb.h: No such file or directory
compilation terminated.
make[2]: *** [/home/st/Desktop/system/hdtv/IT9135_SRC/it9135-core.o] Error 1
make[1]: *** [_module_/home/st/Desktop/system/hdtv/IT9135_SRC] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.2.0-51-generic-pae'
make: *** [default] Error 2

I've searched for info about dvb-usb.h but haven't found anything useful yet. Anyone got any ideas?

---

