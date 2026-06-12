---
title: "Trouble mounting external hard disk"
date: 2008-05-17
forum: General Help
---

### Post by nkobel003 on 2008-05-17
Hello All,

I have a Western Digital 500 GB external hard drive. It is divided into 5 partitions: an ntfs portion that I mainly use it for, a fat32 that I use for backups, and 3 other fat32's that are empty for future linux installations.

When I plug in the hard drive, it give me this error message:
Quote:
Cannot mount volume
Invalid mount option when attempting to mount the volume 'WD500'.
Here is my fstab
Code:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type> 			<options>  			<dump>  <pass>
proc		/proc		proc			defaults			0	0
/dev/sda3	/media/WD500	ntfs			noauto				0	0
UUID=4d1a7194-1abf-40c1-bdcb-7605a7b4b114 /	ext3    relatime,errors=remount-ro 	0       1
/dev/sda4	/media/BACKUP	fat32			noauto				0	0
UUID=bba55c7f-9c54-46db-bac1-c40df0cb823d none  swap    sw  		    	        0       0
/dev/scd0       /media/cdrom0   			udf,iso9660 user,noauto,exec,utf8 0       0

I was able to mount my drive in 7.10, and for the first couple of boots in 8.04, but now it won't let me at all.

Does anyone have any clues?

Thank you,

Nick

---

### Post by strabes on 2008-05-17
Please plug in the drive, run the following command, and paste its output here. ```
sudo fdisk -l
```
By the way, you /etc/fstab file is just for mounting things on boot, and you needn't add anything to that file unless the drive is permanently connected to your computer. Also, do you have the ntfs-3g package installed? Which version of ubuntu are you using? Which partition are you trying to mount? Can you mount it manually?

---

### Post by nkobel003 on 2008-05-17
Here is what it says when I run fdisk:
```
mannequin@NAMELESS:~$ sudo fdisk -l
[sudo] password for mannequin: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x34fe34fd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         638     5124703+  12  Compaq diagnostics
/dev/sda2   *         639        7611    56010622+   c  W95 FAT32 (LBA)
/dev/sda3            7612       10043    19535040   83  Linux
/dev/sda4           10044       10107      514080   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2        3825    30716280    f  W95 Ext'd (LBA)
/dev/sdb2            3826       59917   450558990    7  HPFS/NTFS
/dev/sdb3           59918       60801     7100730    c  W95 FAT32 (LBA)
/dev/sdb5               2        1276    10241406    6  FAT16
/dev/sdb6            1277        2551    10241406    6  FAT16
/dev/sdb7            2552        3825    10233373+   6  FAT16 
```

ntfs-3g?:         yes
ubuntu version:   hardy
partition:        sdb2
manually mount?:  I've tried right clicking on the drive and select "mount' if that is what you mean.

Thank you,

Nick

---

### Post by nkobel003 on 2008-05-17
Ok, I have a breakthrough...

I simply type sudo mount /dev/sdb2 /media/WD500 and it mounts. What I don't get is why it doesn't automatically mount on startup if plugged in...

Any ideas?

---

