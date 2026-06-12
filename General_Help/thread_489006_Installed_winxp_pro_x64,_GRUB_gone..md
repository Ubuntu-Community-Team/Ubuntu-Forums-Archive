---
title: "Installed winxp pro x64, GRUB gone."
date: 2007-06-30
forum: General Help
---

### Post by strm on 2007-06-30
Hi,
I just installed windows xp pro x64 corp in place of my old windows xp pro installation on the 1st partition of my single hard drive and now it seems as though grub is gone, my computer just boots into windows without giving me the option to boot into ubuntu. The only thing I have tried so far was editing boot.ini to boot from 2nd partition, however that obviously does not work as it tries to go through a windows boot sequence from 2nd partition and just gives me an error that it cannot find the files it needs.

Some help would be appreciated. Thanks.

---

### Post by logos34 on 2007-06-30
> **strm said:**
> Hi,
I just installed windows xp pro x64 corp in place of my old windows xp pro installation on the 1st partition of my single hard drive and now it seems as though grub is gone, my computer just boots into windows without giving me the option to boot into ubuntu. The only thing I have tried so far was editing boot.ini to boot from 2nd partition, however that obviously does not work as it tries to go through a windows boot sequence from 2nd partition and just gives me an error that it cannot find the files it needs.

Some help would be appreciated. Thanks.

Undo the changes you made to boot.ini.  All you need to do is restore grub. winxp overwrote it,

Boot from the ubuntu live cd, load the desktop, open a terminal and type:

**sudo grub**

> **find /boot/grub/stage1**
(enter the output 'hd0,x' in the next command)
> **root (hd0,x)**
> **setup (hd0)**
> **quit**

---

