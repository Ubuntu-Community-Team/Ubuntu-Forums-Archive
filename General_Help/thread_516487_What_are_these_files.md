---
title: "What are these files?"
date: 2007-08-03
forum: General Help
---

### Post by paker on 2007-08-03
I backed up my hard disk to a dvd using MondoResue. After the backup, I compared the archived files on DVD to the ones on the hard disk. The program reports that these files are significantly different:

home/rust/.bash_history
home/rust/.gconfd/saved_state
home/rust/.gconf/apps/nautilus/%gconf.xml
home/rust/.gconf/apps/nautilus/preferences/%gconf. xml
lib/modules/2.6.20-16-generic/volatile/nvidia_new.ko
lib/modules/2.6.20-16-generic/volatile/fcdslusba.ko
lib/modules/2.6.20-16-generic/volatile/fcpci.ko
lib/modules/2.6.20-16-generic/volatile/fcusb.ko
lib/modules/2.6.20-16-generic/volatile/fgkrx.ko
lib/modules/2.6.20-16-generic/volatile/fxusb.ko
lib/modules/2.6.20-16-generic/volatile/nvidia.ko
lib/modules/2.6.20-16-generic/volatile/nvidia_legacy.ko
lib/modules/2.6.20-16-generic/volatile/ath_hal.ko
lib/modules/2.6.20-16-generic/volatile/fcdsl.ko
lib/modules/2.6.20-16-generic/volatile/fcdsl2.ko
lib/modules/2.6.20-16-generic/volatile/fcdslsl.ko
lib/modules/2.6.20-16-generic/volatile/fcdslslusb.ko
lib/modules/2.6.20-16-generic/volatile/fcdslusb.ko
lib/modules/2.6.20-16-generic/volatile/fcdslusb2.ko

Will someone kindly glance through the list and tell me if the differences are major? Rephrased, the likelyhood of successfully restoring the system from the archive? Thanks.

---

### Post by dannyboy79 on 2007-08-03
you would be able to successfully restore your system even if the program is reporting these as different. The first ones in your home directory are only a bash history (like a log file) and some preference type stuff. THen all the rest are the modules that get loaded to volatile when you boot up your system. You'll be fine!

---

### Post by paker on 2007-08-03
Thank you for the reply. I now feel more comfortable to experiment different programs and configurations.

---

