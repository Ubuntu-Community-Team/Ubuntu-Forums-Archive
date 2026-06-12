---
title: "driver for usb-hardlock"
date: 2008-05-15
forum: General Help
---

### Post by cmmozos on 2008-05-15
hi,

I am trying to install a USB-hardlock from Aladdin for local use on ubuntu 8.04. The first step is to compile the driver running a script, but I receive the next error:

cm@cm-laptop:~/aksparlnx-1.6-x86$ sudo sh ./build.sh --install
make -C /lib/modules/2.6.24-16-generic/build here=$(pwd)/ SUBDIRS=$(pwd) modules
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/cm/aksparlnx-1.6-x86/Makefile". Fix it to use EXTRA_CFLAGS. Alto.
make[1]: *** [_module_/home/cm/aksparlnx-1.6-x86] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [kernel26] Error 2
aksparlnx.ko does not exist!
aborting
cm@cm-laptop:~/aksparlnx-1.6-x86$

driver and script: [ftp://ftp.aladdin.com/pub/aladdin.de/hardlock/linux/v1.7/i386/aksparlnx-1.7-i386.tar.gz](ftp://ftp.aladdin.com/pub/aladdin.de/hardlock/linux/v1.7/i386/aksparlnx-1.7-i386.tar.gz)

I would appreciate a lot any help or idea!

thanks.

Carlos Mozos

---

