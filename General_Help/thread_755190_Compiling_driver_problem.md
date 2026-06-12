---
title: "Compiling driver problem"
date: 2008-04-14
forum: General Help
---

### Post by npc100 on 2008-04-14
Hi,

I'm trying to compile the wiimote driver and am having a few problems.

The Makefile is as follows:

> KERNEL_SOURCE = /lib/modules/$(shell uname -r)/build
obj-m := wm.o

all:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
        gcc -Wall -Werror -g -lbluetooth -lm -o wmd wmd.c kmisc.c wiimote.c WiimoteLayer.c

clean:
        make -C /lib/modules/$(shell uname -r)/build M=$(PWD) modules
        rm -f *.o wmd Module.symvers


and I get the following error:

> make -C /lib/modules/2.6.22-14-generic/build M=/home/neil/wii_source modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/neil/wii_source/wm.o
/home/neil/wii_source/wm.c:18:24: error: linux/init.h: No such file or directory
/home/neil/wii_source/wm.c:19:26: error: linux/module.h: No such file or directory
/home/neil/wii_source/wm.c:20:26: error: linux/kernel.h: No such file or directory
etc. etc. etc.


Its obviously not finding the kernel headers, but an ls of that directory gives me:

> neil@Lister:/lib/modules/2.6.22-14-generic/build$ ls
arch    Documentation  include  Kbuild  Makefile        net       sound
block   drivers        init     kernel  mm              scripts   usr
crypto  fs             ipc      lib     Module.symvers  security


and under include/linux all the headers are there.

Any help much appreciated. Thanks!

---

