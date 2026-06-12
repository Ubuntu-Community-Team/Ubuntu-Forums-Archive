---
title: "[SOLVED] kernel can't find hdd on boot"
date: 2008-07-09
forum: General Help
---

### Post by Gunman1982 on 2008-07-09
Hi I hope someone can feed me more ideas or a solution. Yesterday my laptop crashed and I had to shut it down the bad way (pressing power button until shutdown). Afterwards I wanted to boot the kernel like always but it told me that the journaling system of my '/root' partition was corrupted and that I should run e2fsck -b 8193 on /dev/hda the problem now was: there is/was no /dev/hda. All there is in in dev are 'loop', 'null' and some tty devices. So it seems that the kernel doesn't see the hdd. But if I type in mount I can see that '/dev/hda4' is mounted on '/' which is right. 

I already tried to
-reinstall grub (with supergrub)
-recreate the boot partition ('/boot')
-checked the journaling of '/boot' and '/' partitions with livedisc
-changed the identifier from hda to sda (since the ubuntu livedisc recognizes my hdd as sda instead of hda) in 'fstab' and 'menu.lst'

Any new ideas, suggestions, help is really welcome but please no suggestions like: "Reformat everything and reinstall"

Oh some further information:
fdisk -l /dev/sda
Disk /dev/sda: 72.2 GB, 72249990144 bytes
255 heads, 63 sectors/track, 8783 cylinders
Units = cylinder of 16065 × 512 = 8225280 bytes
Disk identifier: 0xc646c646

   Device  Boot.     Start        End     Blocks   Id  System
/dev/sda1   *           1        3681    29567601    7  HPFS/NTFS
/dev/sda2            3682        3687       48195   83  Linux
/dev/sda3            3688        3749      498015   82  Linux Swap / Solaris
/dev/sda4            3750        8783    40435605   83  Linux

where
/dev/sda2 is my /boot partition
/dev/sda3 is my swap
/dev/sda4 is my /
and of course /dev/sda1 is the cursed windows

the entries of /boot/grub/menu.lst:
title           Debian GNU/Linux, kernel 2.6.25.10
root            (hd0,1)
kernel          /vmlinuz-2.6.25.10 clocksource=acpi_pm root=/dev/hda4 ro
boot

title           Debian GNU/Linux, kernel 2.6.24.3
root            (hd0,1)
kernel          /vmlinuz-2.6.24.3 clocksource=acpi_pm root=/dev/hda4 ro
boot

title           Microsoft Windows
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by Gunman1982 on 2008-07-09
Solved :biggrin:
For the record: It was a problem with the insalled udev version I don't know if version 0.124-1 (on debian) was buggy or if the files were corrupted however installing 0.124-2 of udev solved the problem. Would like to thank myself for that ... mhhh ... well I guess I just go for a celebration beer :biggrin:

---

