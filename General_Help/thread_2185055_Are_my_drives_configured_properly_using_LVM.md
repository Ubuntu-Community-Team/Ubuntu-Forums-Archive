---
title: "Are my drives configured properly using LVM?"
date: 2013-10-31
forum: General Help
---

### Post by lchalupa on 2013-10-31
I recently went to update my server running 12.10 to 13.04.  The update threw up and sent me to $grub rescue.  Obviously something was not right.
I have since fixed this issue and my server is booting up once again.
The server has  two drives on it: 80GB and 500GB .  When it was installed two years ago I wanted the OS on the 80GB drive and the data on the 500 GB drive.
It also says that it's using LVM.

Could someone help look at the details and help me determine if the drives are configured correctly?
Why would the two drives have two drives with the same UUID?  How will this effect the behavior of the drives?  How do I rectify the situation?

Here are some details.  If you want more data, tell me what you want.

$s udo fdisk -l



Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bdce8


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   156225535    77861889    5  Extended
/dev/sda5          501760   156225535    77861888   8e  Linux LVM


Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000bdce8


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048      499711      248832   83  Linux
/dev/sdb2          501758   156225535    77861889    5  Extended
/dev/sdb5          501760   156225535    77861888   8e  Linux LVM


Disk /dev/mapper/purple-root: 60.4 GB, 60372811776 bytes
255 heads, 63 sectors/track, 7339 cylinders, total 117915648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/purple-root doesn't contain a valid partition table


Disk /dev/mapper/purple-swap_1: 19.3 GB, 19323158528 bytes
255 heads, 63 sectors/track, 2349 cylinders, total 37740544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/mapper/purple-swap_1 doesn't contain a valid partition table

****************** end of fdisk listing  ***************************************

$ sudo  pvscan 
lchalupa@purple:~$ sudo pvscan
  Found duplicate PV 69MbuN0JadaQ2l1Ci1WjNv0xN4xkhuAa: using /dev/sdb5 not /dev/sda5
  PV /dev/sdb5   VG purple   lvm2 [74.25 GiB / 32.00 MiB free]
  Total: 1 [74.25 GiB] / in use: 1 [74.25 GiB] / in no VG: 0 [0   ]

***************** end of pvscan *************************************************

$ sudo lvscan
lchalupa@purple:~$ sudo lvscan
  Found duplicate PV 69MbuN0JadaQ2l1Ci1WjNv0xN4xkhuAa: using /dev/sdb5 not /dev/sda5
  ACTIVE            '/dev/purple/root' [56.23 GiB] inherit
  ACTIVE            '/dev/purple/swap_1' [18.00 GiB] inherit

****************end of lvscan **************************************************




What is wrong with this picture?
What do I do to fix it?

Thanks

Lee

---

