---
title: "Step to build USB bootable device"
date: 2006-12-31
forum: General Help
---

### Post by moonhk on 2006-12-31
Hi Reader

Base on Ubuntu Installation Guid (This document contains installation instructions for the Ubuntu 6.06 LTS system, in install CD-ROM ) 4.3. Preparing Files for USB Memory Stick Booting

I take following steps to build USB Memory Stick Booting 
step 1. mkdosfs /dev/sdb1
Step 2 install-mbr /dev/sdb1
Step 3 zcat boot.img.gz > /dev/sdb1 # boot.img.gz download base on installation Guid.

The disable all harddisk, try to boot the USB. My computer no response. No error message prompted. Do you know what step is missing ? 


root@hex:/home/moonhk/data# uname -a
Linux hex 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux
root@hex:/home/moonhk/data#

---

### Post by majoridiot on 2007-01-01
do you have usb enabled for boot and in the boot drive sequence in bios?

---

### Post by meng on 2007-01-01
Not all BIOSes support booting from USB. Hopefully yours does.

---

### Post by moonhk on 2007-01-01
My Two computer BIOS support boot by USB-ZIP and USB-HDD

---

### Post by gn2 on 2007-01-01
PCLinuxOS has install to USB as an option during the normal install process, and it works perfectly.

---

### Post by moonhk on 2007-01-13
I tested. Only one New computer spport boot by USB-HDD
Other old computer say support boot by USB-ZIP is not correct.

---

