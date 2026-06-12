---
title: "Recover corrupted partition (table) after resizing partition"
date: 2015-12-26
forum: General Help
---

### Post by berkieboy on 2015-12-26
I have a dual boot Windows 7 (sda2) / Ubuntu 12.04 (sda5).
[LIST]
[*]I recently encountered an error in the boot loader GRUB so I used [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair#Recommended_repair"). This was done successfully. 
[*]Then I decided to shrink my ntfs partition to create unallocated  space (The latter I would use to finally extend my sda5 partition). Therefore I used bootable [Minitool Partition Wizard]("http://www.partitionwizard.com/free-partition-manager.html"). However when I moved the unallocated space I received an I/O error and ended up with unallocated space and a 'disappeared' ext4 partition. I tried the recover the lost partition with Minitool Partition Wizard, but that didn't work. 
[*]Fortunaly Boot Repair made a log file with the information from 
[/LIST]
[INDENT]**fdisk -l**
[/INDENT]
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd246975f

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          501760  1863630847   931564544    7  HPFS/NTFS/exFAT
/dev/sda3      1908504576  1953523711    22509568   27  Hidden NTFS WinRE
/dev/sda4      1863632894  1908504575    22435841    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1863632896  1892818943    14593024   83  Linux
/dev/sda6      1892820992  1908504575     7841792   82  Linux swap / Solaris
```[INDENT]**blkid**
[/INDENT]
 ```

/dev/loop0: TYPE="squashfs"
/dev/sda1: LABEL="SYSTEM" UUID="04F2AE77F2AE6D1C" TYPE="ntfs"
/dev/sda2: UUID="01CF2E1573431200" TYPE="ntfs"
/dev/sda3: LABEL="SAMSUNG_REC" UUID="C86C18876C187304" TYPE="ntfs"
/dev/sda5: UUID="38daf5f9-ab64-4c83-9f61-14514d52fffa" TYPE="ext4"
/dev/sda6: UUID="05cb3b97-f9cd-472f-9f4a-249fb96f568b" TYPE="swap"


```


[LIST]
[*]I decided to delete all partitions fdisk command d, recreate all partitions using command n and finally setting system type of every partition with command t (info from log file Boot repair) 
[/LIST]
[INDENT]**fdisk -l**
[/INDENT]
```
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0xd246975f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS/exFAT
/dev/sda2          501760  1863630847   931564544    7  HPFS/NTFS/exFAT
/dev/sda3      1908504576  1953523711    22509568   27  Hidden NTFS WinRE
/dev/sda4      1863632894  1908504575    22435841    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1863632896  1892818943    14593024   83  Linux
/dev/sda6      1892820992  1908504575     7841792   82  Linux swap / Solaris

Partition table entries are not in disk order

```

however **lsblk -f**
```
 
NAME   FSTYPE   LABEL       MOUNTPOINT
sda                         
&#9500;&#9472;sda1 ntfs     SYSTEM      
&#9500;&#9472;sda2 ntfs                 /media/lubuntu/01D13F335573F600
&#9500;&#9472;sda3 ntfs     SAMSUNG_REC 
&#9500;&#9472;sda4[B]                      
&#9500;&#9472;sda5  [/B]                    
&#9492;&#9472;sda6 swap                 [SWAP]

 
```
shows no file type for sda5

**blkid**
```
 /dev/loop0: TYPE="squashfs" 
/dev/loop1: UUID="6a575cac-ea16-4b91-bc63-c453dabe2351" TYPE="ext3" 
/dev/sda1: LABEL="SYSTEM" UUID="04F2AE77F2AE6D1C" TYPE="ntfs" 
/dev/sda2: UUID="**01D13F335573F600**" TYPE="ntfs" 
/dev/sda3: LABEL="SAMSUNG_REC" UUID="C86C18876C187304" TYPE="ntfs" 
/dev/sda6: UUID="05cb3b97-f9cd-472f-9f4a-249fb96f568b" TYPE="swap" 


```
shows a different UUID for sda2 (Windows partition), however is successfully mounted when I start with an Lubuntu live cd.
 
How can i fix this problem so i can recover my data from partition Ubuntu sda5?

---

