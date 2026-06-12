---
title: "BOOT subtle mess"
date: 2007-12-28
forum: General Help
---

### Post by Kalidor on 2007-12-28
I had windows XP and ubuntu. Grub worked perfectly. 
I installed windows SVISTA 64bit instead of windows xp and of course ripped grub open in the process. Then i used the alternate installation cd of ubuntu 7.10 which I made a mess with and I think   (notice I wrote that "I Think") I installed grub  on dev/sda2 if i remember correctly.  Then i edited grub with qgrubeditor and created a vista  entry in the boot menu, which of course did not work in the sense that it did not allow me to chose vista. Ubuntu still works. If i write find boot/grub/stage1from terminal  it tells me "error 15 File not found". Now never mind the qgrub editor stuff. The partition with windows is (hd0,0) i guess. How do I fix the boot from ubuntu?

---

### Post by logos34 on 2007-12-28
post the output from

sudo fdisk -l

---

### Post by Kalidor on 2007-12-28
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12281227

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10711    86036076    7  HPFS/NTFS
/dev/sda2           10712       19160    67866592+  83  Linux
/dev/sda3           19161       19457     2385652+   5  Extended
/dev/sda5           19161       19457     2385621   82  Linux swap / Solaris

---

### Post by logos34 on 2007-12-28
yep, windows is (hd0,0)

Sometimes Vista doesn't want to play nice with grub, in which case you have to use vista bootloader to boot linux.

Your windows entry should look like this:

> title		Windows Vista
root		(hd0,0)
savedefault
makeactive
chainloader	+1

*or **rootnoverify (hd0,0)**

But if that's what you tried then go the EasyBCD route:
[http://neosmart.net/wiki/display/EBCD/linux](http://neosmart.net/wiki/display/EBCD/linux)

(you'll obviously have to use the vista install dvd to restore the vista boot manager to get into vista to install easybcd)

---

### Post by Kalidor on 2007-12-28
this way of settin up the entry does not work i'll try your way

---

