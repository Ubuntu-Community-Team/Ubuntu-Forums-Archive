---
title: "Grub error 22"
date: 2007-01-03
forum: General Help
---

### Post by keshek on 2007-01-03
I am trying to install Ubuntu 6.10 and I am having a problem booting after the install. I get a Grub error 22 when it tries to boot. This is what I get from fdisk -l 

```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       15681   125957601    7  HPFS/NTFS
/dev/sda2   *       15682       19299    29061585   83  Linux
/dev/sda3           19300       19457     1269135    5  Extended
/dev/sda5           19300       19457     1269103+  82  Linux swap / Solaris

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       24320   195350368+   7  HPFS/NTFS

Disk /dev/hdd: 80.0 GB, 80026361856 bytes
236 heads, 43 sectors/track, 15402 cylinders
Units = cylinders of 10148 * 512 = 5195776 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1   *           1       15402    78146560    7  HPFS/NTFS

```

This is a dual boot system with both WinXp and Ubuntu being installed to my first Serial ATA hd. I let the installer partition the free space for Ubuntu and accepted the default install location for grub which was hd0. I have installed ubuntu in the past without any problems using the exact same setup. But I always used the text based installers. Just to check I pulled out my 6.06 dvd and ran the text installer and used the same partition setup (it doesnt ask where to install grub) and the installer froze at installing grub. Could anyone tell me what I should enter for grub location to get this install to work. Thanks.

---

### Post by nrwilk on 2007-01-03
Here's a list of grub errors:
[http://www.uruk.org/orig-grub/errors.html](http://www.uruk.org/orig-grub/errors.html)


Here's number 22 of that list:

[quote=http://www.uruk.org/orig-grub/errors.html]22 : "Must load Multiboot kernel before modules"

This error is returned if the module load command is used before loading a Multiboot kernel. It only makes sense in this case anyway, as GRUB has no idea how to communicate the presence of location of such modules to a non-Multiboot-aware kernel.[/quote]

Good luck interpreting it.  I have no idea what it means. :-k 

Sorry!

nrwilk

---

### Post by keshek on 2007-01-03
I found the problem, I checked the bios and the hard drives were booting in the wrong order, I switched the IDE hd to the first and now it works.

---

