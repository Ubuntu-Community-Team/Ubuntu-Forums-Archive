---
title: "trouble mounting NTFS raid 5"
date: 2008-05-02
forum: General Help
---

### Post by mini98tacoma on 2008-05-02
Hello all I am just switching other to linux via Hardy Heron. I have gotten everything setup except I can't for the life of me mount my NTFS raid array for my media center storage. I am running XP MC in virtual box and about to startup a webserver in another virtual box. I would like to keep Heron has my host for virtual box, but I can't mount my nvidia raid array. If anyone can help I would greatly appreciate it. I have tried everything that has come up in my searching so this is my cry for help.

The box is running an Asus M2N Sli Deluxe board with 5 Sata drives.
1 80gb drive dual booting Media Center and Hardy Heron.

4 250gb drive in a RAID 5 (this array is the one I can't mount.

Here is what I get when I run dmraid and fdisk -l.

**FDISK -l**

[I]Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0fb22904

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       91203   732588066    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1eb67392

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488392033+   7  HPFS/NTFS

Disk /dev/sdc: 250.0 GB, 250059350016 bytes
16 heads, 63 sectors/track, 484521 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0x840e4e33

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1     1871424   943197171    6  FAT16

Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x950a14a5

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x45854584

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         122      979933+  82  Linux swap / Solaris
/dev/sde2             123        1338     9767520   83  Linux
/dev/sde3   *        1339        2554     9767520    7  HPFS/NTFS[/I]

**DMRAID -TAY**

*nvidia_ffcchdef: 0 1465191168 raid45 core 2 131072 nosync raid5_ls 1 128 4 -1 /dev/sda 0 /dev/sdb 0 /dev/sdd 0 /dev/sdc 0*

-----------------
**Things I have Tried**
-----------------

*sudo mount -t ntfs-3g /dev/mapper/nvidia_ffcchdef /media/storage*

**it returns**

[I]ntfs-3g: Failed to access volume '/dev/mapper/nvidia_ffcchdef': No such file or directory
[/I]

If I try to mount it in the GUI I get a return that I am not privilaged.

any suggestions are welcome

---

### Post by mini98tacoma on 2008-05-02
I think I found my problem.

if i run 

DMRAID -AY i get a raid45 not in kernel.

I am going to stop this thread and search for info on patching my kernel with raid45.

If you have any help PM i dont know how to patch a kernel but hey I am up for learning.

---

### Post by dannns on 2008-05-02
Ok, I was looking into the same. The posts from Stefan and Prince in here [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220493](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220493) helped a lot. With Stefan's sources added it worked! At least I was able to mount the partition, now I need to figure out how to mount it on start up.

---

