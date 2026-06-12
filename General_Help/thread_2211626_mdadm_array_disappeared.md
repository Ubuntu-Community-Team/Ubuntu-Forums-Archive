---
title: "mdadm array disappeared"
date: 2014-03-16
forum: General Help
---

### Post by ris8 on 2014-03-16
I was moving my mdadm array from my old machine to a new one. As the new one was not able to see it, I tried to put it back, but I seem to have lost all superblocks. Only 1 drive has a partition. Help!
(I have backups of the most important stuff... but I'd rather not try to see if the backups worked)

running ubuntu server 13.10

array comprises 4 HDD of 3TB each, in raid10. This is my data drive, not the boot

cat /proc/partitions shows all 4 drives (sda-c-d-e)
```
cat /proc/partitions
major minor  #blocks  name
  11        0    1048575 sr0
   8        0 2930266584 sda
   8        1 2930265543 sda1
   8       16   78150744 sdb
   8       17     102400 sdb1
   8       18   69854208 sdb2
   8       19          1 sdb3
   8       21    2532352 sdb5
   8       22     308224 sdb6
   8       23    5349376 sdb7
   8       32 2930266584 sdc
   8       48 2930266584 sdd
   8       64 2930266584 sde
   8       80  244198584 sdf
   8       81   97659103 sdf1
   8       82          1 sdf2
   8       83   51199155 sdf3
   8       85    9936171 sdf5

```

dmesg does not show anything odd:
```

dmesg | grep sdd
[    1.400539] sd 2:0:0:0: [sdd] 5860533168 512-byte logical blocks: (3.00 TB/2.
72 TiB)
[    1.400544] sd 2:0:0:0: [sdd] 4096-byte physical blocks
[    1.400573] sd 2:0:0:0: [sdd] Write Protect is off
[    1.400577] sd 2:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    1.400590] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, does
n't support DPO or FUA
[    1.463874]  sdd:
[    1.463970] sd 2:0:0:0: [sdd] Attached SCSI disk

```

blkid does not show any member 
```

sudo blkid
/dev/sdb1: LABEL="System Reserved" UUID="D8822F92822F7462" TYPE="ntfs"
/dev/sdb2: UUID="623C39873C3956EF" TYPE="ntfs"
/dev/sdb5: UUID="7faf4a24-3091-40bb-9c89-0b323d1f8202" TYPE="ext4"
/dev/sdb6: UUID="59300063-93fd-4ffb-9956-51c2f7acc106" TYPE="swap"
/dev/sdb7: UUID="2ddd72e7-e761-4404-8843-b3d9262e99ff" TYPE="ext4"
/dev/sdf1: UUID="3bec1677-d3ae-4045-b60b-8aa7e72b3b26" SEC_TYPE="ext2" TYPE="ext
3"
/dev/sdf3: UUID="06701150701147B7" TYPE="ntfs"
/dev/sdf5: UUID="ed3ff2ab-29c9-471c-b67c-f6bcd75a9768" TYPE="swap"

```

parted shows something for sda, but no the others
```

sudo parted -l
Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sda: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system  Name        Flags
 1      1049kB  3001GB  3001GB               Linux RAID  raid



Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdc: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sdd: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags


Model: ATA WDC WD30EFRX-68A (scsi)
Disk /dev/sde: 3001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start  End  Size  File system  Name  Flags

```

no superblocks
```

sudo mdadm --examine /dev/sd[acde]
/dev/sda:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdc:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sdd:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)
/dev/sde:
   MBR Magic : aa55
Partition[0] :   4294967295 sectors at            1 (type ee)

sudo mdadm --examine /dev/sd[acde]1
mdadm: No md superblock detected on /dev/sda1.

```

Little more, probably un-necessary background
The original server died a couple of weeks ago, and what I call the "old" server above is a temporary dual boot of my htpc. So a fresh 13.10 install. This was working fine

Not sure about the issues with the new server where I was moving the array... maybe related to the Marvell SE9172 chipset, which apparently causes issues in linux, or to the old SSD where I had put the O/S
At the first boot attempts on the new server, mdadm complained about the degraded array (since 2 drives were on the marvell sata). Once I shuffled the connections LVM would complain about the root volume missing. So I put all disks back in the original machine (the dual boot htpc) and discovered all was missing...

---

