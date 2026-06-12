---
title: "make error"
date: 2007-06-07
forum: General Help
---

### Post by Vladimirm on 2007-06-07
I'm trying to install the RT61 drivers, following this  [guide]("http://ubuntuforums.org/showthread.php?t=132980") for my wireless card and i've tried a 'make all' and i get this error message

> :~/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module$ sudo make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/vladimirm/Desktop/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2


help..?

---

### Post by renzokuken on 2007-06-07
have you installed the make tools and the compilers?

if not run

```
sudo apt-get install build-essential
``` (i'm assuming you have a working net connection here)

---

### Post by Vladimirm on 2007-06-07
Installed build-essential and get

> ~/RT61_Linux_STA_Drv1.1.0.0/Module$ make all
make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  CC [M]  /home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o
/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_probe’:
/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:197: error: ‘struct net_device’ has no member named ‘get_wireless_stats’
/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c: In function ‘RT61_open’:
/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.c:326: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
make[2]: *** [/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module/rtmp_main.o] Error 1
make[1]: *** [_module_/home/vladimirm/RT61_Linux_STA_Drv1.1.0.0/Module] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [all] Error 2

---

### Post by renzokuken on 2007-06-08
is "make all" the only command you are running?

the usual steps for compiling from source are

```
./configure
make
**sudo** make install
```

check the readme/install file

---

