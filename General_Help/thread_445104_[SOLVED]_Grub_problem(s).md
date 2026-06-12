---
title: "[SOLVED] Grub problem(s)"
date: 2007-05-15
forum: General Help
---

### Post by MadMac on 2007-05-15
Howdy!

When I boot up/restart, I get an Error 18 or an Error 16 or it starts up okay. If I get an error 16 or 18 and hit the enter key it comes back with an Error 16 or an Error 18 or a Startup. If I have to hit the enter key yet again I will either get another Error 16 or 18 or it will continue booting into Ubuntu. No rhyme or reason as to which error I get or when it will decide to continue booting. Eventually, it will boot, though.

I did try the fix grub thing where you boot from the CD and run the commands to fix grub - [http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub](http://ubuntuforums.org/showthread.php?t=224351&highlight=restore+grub) - no joy.

The BIOS is from October of last year (2006) so that shouldn't be a problem, I believe. It is an Intel CPU, 3.20 Ghz, with 1024 RAM.

Below is my fdisk -l and grub check. Any help on how to fix this is appreciated! Thanks!

========================
fdisk -l:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9728    78140128+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4660    37431418+  83  Linux
/dev/sdb2            4661        4865     1646662+   5  Extended
/dev/sdb5            4661        4865     1646631   82  Linux swap / Solaris

Disk /dev/sdc: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdd: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       12160    97675168+   7  HPFS/NTFS


========================

grub> find /boot/grub/stage1
(hd3,0)
========================

Anyone?

Thanks!

---

### Post by MadMac on 2007-05-18
Anyone have any ideas on this, please?

---

### Post by MadMac on 2007-06-12
Bump this up here so someone may read it...

---

