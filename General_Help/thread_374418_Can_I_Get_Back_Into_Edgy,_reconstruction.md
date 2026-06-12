---
title: "Can I Get Back Into Edgy, reconstruction"
date: 2007-03-02
forum: General Help
---

### Post by Chazall1 on 2007-03-02
I thought I had educated myself to make it all work. I had a Single dual boot Edgy and XP. Both Harddrives are IDE, Primary Master, Ubuntu and Primary Slave XP. My xp boots fine, I used the Super Grub Disk to fixmbr. Did the Edgy Live CD to install Grub setup (hd0) all went well.
On the first boot I had my Grub Screen with all the operating systems available, I wanted to checkout XP and everything was fine. I re-booted to check out Edgy, and Grub did not show up and I was booting back to XP. 

During my computer transformation, I forgot to add the three partitions from the XP on hda1,
hda2, and hda3 which were copied from hda to hdb. If the partition #'s are off from my original root (0,5) this would explain why I can not get access to Edgy. I tried the Super Grub Disk, no luck. I went back to Gparted and adder 3 Primary partitions to see if this would correct the Issue?  

Here is my fdisk -lu  My original config was hda4 - hda7, 
How can I get or Mount to change my Fstab and Grub menu.lst???????
Also, I did use the ## to comment out the old mount points for my WINXP
Can I get back into my Edgy???
Can you assist

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    22426739    11213338+  83  Linux
/dev/hda2        22426740    44949869    11261565   83  Linux
/dev/hda3        44949870    68774264    11912197+  83  Linux
/dev/hda4        68774265   156248189    43736962+   5  Extended
/dev/hda5        68774328   111989114    21607393+  83  Linux
/dev/hda6       111989178   154143674    21077248+  83  Linux
/dev/hda7       154143738   156248189     1052226   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63       96389       48163+  de  Dell Utility
/dev/hdb2   *       96390   101000654    50452132+   7  HPFS/NTFS
/dev/hdb3       101000655   106767989     2883667+   b  W95 FAT32

---

### Post by dcstar on 2007-03-02
> **Chazall1 said:**
> I thought I had educated myself to make it all work. I had a Single dual boot Edgy and XP. Both Harddrives are IDE, Primary Master, Ubuntu and Primary Slave XP. My xp boots fine, I used the Super Grub Disk to fixmbr. Did the Edgy Live CD to install Grub setup (hd0) all went well.
On the first boot I had my Grub Screen with all the operating systems available, I wanted to checkout XP and everything was fine. I re-booted to check out Edgy, and Grub did not show up and I was booting back to XP. 

During my computer transformation, I forgot to add the three partitions from the XP on hda1,
hda2, and hda3 which were copied from hda to hdb. If the partition #'s are off from my original root (0,5) this would explain why I can not get access to Edgy. I tried the Super Grub Disk, no luck. I went back to Gparted and adder 3 Primary partitions to see if this would correct the Issue?  

Here is my fdisk -lu  My original config was hda4 - hda7, 
How can I get or Mount to change my Fstab and Grub menu.lst???????
Also, I did use the ## to comment out the old mount points for my WINXP
Can I get back into my Edgy???
Can you assist

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/hda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63    22426739    11213338+  83  Linux
/dev/hda2        22426740    44949869    11261565   83  Linux
/dev/hda3        44949870    68774264    11912197+  83  Linux
/dev/hda4        68774265   156248189    43736962+   5  Extended
/dev/hda5        68774328   111989114    21607393+  83  Linux
/dev/hda6       111989178   154143674    21077248+  83  Linux
/dev/hda7       154143738   156248189     1052226   82  Linux swap / Solaris

Disk /dev/hdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1              63       96389       48163+  de  Dell Utility
/dev/hdb2   *****       96390   101000654    50452132+   7  HPFS/NTFS
/dev/hdb3       101000655   106767989     2883667+   b  W95 FAT32

There is no partition on the first disk marked as the boot partition (identified by the "*"), so unless you set the partition where you installed Grub as the boot partition, then Grub cannot boot!

BTW, fixmbr wipes out Grub, so if that is what you did after installing Grub on the XP partition then your problem has been explained.

---

