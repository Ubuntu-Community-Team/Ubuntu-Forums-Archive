---
title: "Grub error 17"
date: 2007-01-14
forum: General Help
---

### Post by jcgg on 2007-01-14
I have three 80 gb hard drives. First drive has XP 32 bit installed, 2nd drive has XP 64 bit, 3rd drive has tow XP partiions and Kubuntu is installed on the 3rd partition of the tird drive. Upon rebooting I receive an error 17. Here is the answer to the usual questions. Any help is greatly appreciated.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/hda2            2551        9728    57657285    f  W95 Ext'd (LBA)
/dev/hda5            2551        5100    20482843+   7  HPFS/NTFS
/dev/hda6            5101        9728    37174378+   7  HPFS/NTFS

Disk /dev/hdb: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       10011    80413326    7  HPFS/NTFS

Disk /dev/hdc: 80.0 GB, 80026361856 bytes
16 heads, 63 sectors/track, 155061 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1       37587    18943816+   7  HPFS/NTFS
/dev/hdc2           37588      109105    36045072    7  HPFS/NTFS
/dev/hdc3   *      109109      153112    22177732+  83  Linux
Partition 3 does not end on cylinder boundary.
/dev/hdc4          153112      155056      979965    5  Extended
Partition 4 does not end on cylinder boundary.
/dev/hdc5          153112      155056      979933+  82  Linux swap / Solaris
ubuntu@ubuntu:~$ gksudo gedit /boot/grub/menu.lst
bash: gksudo: command not found
ubuntu@ubuntu:~$ cat /boot/grub/device.map
cat: /boot/grub/device.map: No such file or directory
ubuntu@ubuntu:~$

---

### Post by Sef on 2007-01-14
> Device Boot Start End Blocks Id System
/dev/hda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/hda2 2551 9728 57657285 f W95 Ext'd (LBA)
/dev/hda5 2551 5100 20482843+ 7 HPFS/NTFS
/dev/hda6 5101 9728 37174378+ 7 HPFS/NTFS

> Device Boot Start End Blocks Id System
/dev/hdc1 1 37587 18943816+ 7 HPFS/NTFS
/dev/hdc2 37588 109105 36045072 7 HPFS/NTFS
/dev/hdc3 * 109109 153112 22177732+ 83 Linux
Partition 3 does not end on cylinder boundary.
/dev/hdc4 153112 155056 979965 5 Extended
Partition 4 does not end on cylinder boundary.
/dev/hdc5 153112 155056 979933+ 82 Linux swap / Solaris

Looks like you have two boots set up.   Remove the one from /dev/hdc3 and see if that resolves your problem.   GRUB should pick up all of your operating systems.

---

### Post by jcgg on 2007-01-14
Thank you for the help. I do have two follow up questions:

1. How do remove hdc3 as a boot;
2. How did you come to the conclusion from reviewing my post that hdc3 was the problem.

Thanks.

---

### Post by Negative on 2007-01-14
Forgive my newness, as I am not an Ubuntu guy yet.  But I have had the same exact error.

The problem stems from Grub not playing well with 64bit LVM systems.  I was told it couldn't be done, but I found a way, perhaps it will work for you.

Although I only had 2 drives, but the idea should be the same.

First I unplugged all the other drives except the one I had FC installed on, and installed Grub on that drive (in your case the 3rd one).  Grub couldn't see the WinXP drive so it didn't install it on the MBR.  Once I got into FC and got everything set up, I powered down and reconnected my other drive, this then booted the WinXP HD without problem.  I rebooted and went into BIOS setup and switched primary drive there to HD2 and loaded FC without problems.  (Note not changing on the motherboard, just in setup) Once back in FC I edited the grub.conf file to map hd2 to hd1 and then hd1 to hd2, and added the WinXP info to Grub (rootnoverify +1, etc..)

Leaving HD2 as primary in BIOS, I restarted and WinXP and FC showed up in Grub and both were selectable and booted fine.

Good Luck, it took me about 3 weeks to find this one out :D

Neg

---

