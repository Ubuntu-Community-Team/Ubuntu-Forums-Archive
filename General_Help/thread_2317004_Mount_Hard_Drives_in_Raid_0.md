---
title: "Mount Hard Drives in Raid 0"
date: 2016-03-12
forum: General Help
---

### Post by stefan40 on 2016-03-12
[COLOR=#222426][FONT=Arial]I used 2x 4TB Hard Drives in my Synology NAS in Raid 0. After buying a new NAS, I wanted to copy the data directly from the hard drives to my Ubuntu Machine, so I attached them via SATA. Now I am stuck since the Hard Drives do not mount because of "wrong fs type, bad option, bad superblock".[/FONT][/COLOR]
[COLOR=#222426][FONT=Arial]This is my fisk Output:

[/FONT][/COLOR]
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4000.8 GB, 4000787030016 bytes
255 heads, 63 sectors/track, 486401 cylinders, total 7814037168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT
Partition 1 does not start on physical sector boundary.

WARNING: GPT (GUID Partition Table) detected on '/dev/sdc'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00089444

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1   234441647   117220823+  ee  GPT

Disk /dev/md127: 542 MB, 542834688 bytes
2 heads, 4 sectors/track, 132528 cylinders, total 1060224 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x6567bcc3

Disk /dev/md127 doesn't contain a valid partition table

Disk /dev/md126: 542 MB, 542769152 bytes
2 heads, 4 sectors/track, 132512 cylinders, total 1060096 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md126 doesn't contain a valid partition table

Disk /dev/md125: 469 MB, 469893120 bytes
2 heads, 4 sectors/track, 114720 cylinders, total 917760 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

Disk /dev/md125 doesn't contain a valid partition table

[COLOR=#222426][FONT=Arial]After executing the steps from the Synology website ([synology.com/en-us/knowledgebase/DSM/tutorial/Storage/&#8230;]("https://www.synology.com/en-us/knowledgebase/DSM/tutorial/Storage/How_can_I_recover_data_from_my_DiskStation_using_a_PC")) the Disk tool show that both drives have 2 Linux Raid Member Partitions (SDA1 and SDA2) which are both around 500MB and then the 4TB Ext4 (SDA3) Partition. The Raid Array that has been created is 543 MB but only contains several packages.
[/FONT][/COLOR][IMG]https://i.imgsafe.org/2ebd6fd.png[/IMG]
[IMG]https://i.imgsafe.org/7401531.png[/IMG]

---

