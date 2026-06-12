---
title: "liveusb of gutsy boots but can't find /lib/modules/2.6.22-12-generic/modules"
date: 2007-09-30
forum: General Help
---

### Post by delfick on 2007-09-30
hello, 

I've installed gutsy onto my usb using this guide here [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/)

and it boots :D

but when it does, it doesn't work...

it comes up saying
> **"thescreen"]BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu4) Built-in shell (ash)
Enter 'help' for a list of built-in commands

/bin/sh:can't access tty said:**
> 

when i go to tty1 (after pressing <ctrl><Alt>F1 , it tells me

[quote]Warning: Couldn't open directory /lib/modules/2.6.22-12-generic/: No such file or directory
FATAL: Could not open  /lib/modules/2.6.22-12-generic/modules.dep.temp: No such file or directory
FATAL: Could not open  /lib/modules/2.6.22-12-generic/modules.dep: No such file or directory
FATAL: Could not open  /lib/modules/2.6.22-12-generic/modules.dep: No such file or directory

does anyone know what could have gone wrong ?? 

thnx :D

---

### Post by delfick on 2007-10-01
problem solved, the guide tells you to put in their version of initrd.gz which contains an old version of the kernel......

putting in the original initrd.gz and following this [http://ubuntuforums.org/showpost.php?p=3228722&postcount=157](http://ubuntuforums.org/showpost.php?p=3228722&postcount=157) seems to work :D

---

