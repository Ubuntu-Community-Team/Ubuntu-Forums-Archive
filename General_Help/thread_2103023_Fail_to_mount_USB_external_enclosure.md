---
title: "Fail to mount USB external enclosure"
date: 2013-01-09
forum: General Help
---

### Post by satimis on 2013-01-09
Hi all,

Ubuntu 12.04 desktop 64bit

For unknown reason the USB external enclosue fails to mount automatically.  

Warning:```

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

$ dmesg | tail```

[   79.774909] sd 3:0:0:0: [sdc] Assuming drive cache: write through
[   79.774915] sd 3:0:0:0: [sdc] Attached SCSI disk
[   80.255406] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[   80.255415] EXT2-fs (sdc1): group descriptors corrupted
[  184.852511] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[  184.852520] EXT2-fs (sdc1): group descriptors corrupted
[  532.463987] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[  532.463997] EXT2-fs (sdc1): group descriptors corrupted
[  683.677289] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[  683.677299] EXT2-fs (sdc1): group descriptors corrupted

```

$ sudo fdisk -l```

....
....
Disk /dev/sdc: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00083ffc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048  1250263039   625130496   83  Linux

```


Tried to mount it manually without success.  There is only one partition on the HD

$ sudo mount -t ext2 /dev/sdc1 /mnt```

mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

$ dmesg | tail```

[  532.463987] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[  532.463997] EXT2-fs (sdc1): group descriptors corrupted
[  683.677289] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[  683.677299] EXT2-fs (sdc1): group descriptors corrupted
[ 1116.031557] EXT3-fs (sdc): error: can't find ext3 filesystem on dev sdc.
[ 1116.081689] EXT4-fs (sdc): VFS: Can't find ext4 filesystem
[ 1116.169356] EXT2-fs (sdc): error: can't find an ext2 filesystem on dev sdc.
[ 1133.983241] EXT2-fs (sdc): error: can't find an ext2 filesystem on dev sdc.
[ 1145.519512] EXT2-fs (sdc1): error: ext2_check_descriptors: Block bitmap for group 1794 not in group (block 59244544)!
[ 1145.519521] EXT2-fs (sdc1): group descriptors corrupted

```

Please help.  TIA

satimis

---

### Post by dcstar on 2013-01-09
> **satimis said:**
> 
......
Please help.  TIA

satimis

```
sudo fsck /dev/sdc1
```

---

### Post by satimis on 2013-01-09
> **dcstar said:**
> ```
sudo fsck /dev/sdc1
```
Hi,

Performed following steps;

$ sudo file -s /dev/sdc1```

/dev/sdc1: Linux rev 0.0 ext2 filesystem data (mounted or unclean), UUID=00000000-0000-0000-0000-000000000000 (errors)

```

$ sudo fsck /dev/sdc1```

fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext2: Group descriptors look bad... trying backup blocks...
/dev/sdc1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Inode 15409156 has a extra size (33204) which is invalid
Fix<y>? yes

Inode 15409157 has a extra size (33204) which is invalid
Fix<y>? yes
...
....
.....
Illegal block #8 (1357702771) in inode 20021469.  CLEARED.
Illegal block #9 (1356956940) in inode 20021469.  CLEARED.
Illegal block #10 (1333111983) in inode 20021469.  CLEARED.
Illegal block #813 (1397638477) in inode 20021469.  CLEARED.
Illegal block #830 (1229799685) in inode 20021469.  CLEARED.
Illegal block #831 (1478512460) in inode 20021469.  CLEARED.
Illegal block #832 (892477545) in inode 20021469.  CLEARED.
Illegal block #896 (1247102468) in inode 20021469.  CLEARED.
Illegal block #897 (1431524425) in inode 20021469.  CLEARED.
Illegal block #898 (1162433312) in inode 20021469.  CLEARED.
Illegal block #899 (1397638477) in inode 20021469.  CLEARED.
Too many illegal blocks in inode 20021469.
Clear inode<y>? yes
```

hanging here for >20min

```

Restarting e2fsck from the beginning...
/dev/sdc1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes

Restarting e2fsck from the beginning...
/dev/sdc1 was not cleanly unmounted, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Entry 'Transfer_Directory' in / (2) has deleted/unused inode 15409153.  Clear<y>? yes

Entry 'Inland_Revenue' in /Satimis_Document/Old_n_New_Documents_20121228/Documents_from_20100614_20130109/Doc_Personal_20100614_20130109/Personal_20100614_20130109 (19947693) has deleted/unused inode 20021458.  Clear<y>? yes
....
....
Pass 3: Checking directory connectivity
Pass 3A: Optimizing directories

Pass 4: Checking reference counts
Inode 2 ref count is 8, should be 7.  Fix<y>? yes

Inode 19947693 ref count is 23, should be 21.  Fix<y>? 

Pass 4: Checking reference counts
Inode 2 ref count is 8, should be 7.  Fix<y>? yes

Inode 19947693 ref count is 23, should be 21.  Fix<y>? yes

Inode 19980322 ref count is 7, should be 6.  Fix<y>? yes

Unattached inode 32235521
Connect to /lost+found<y>? yes

Inode 32235521 ref count is 2, should be 1.  Fix<y>? 

Pass 5: Checking group summary information
Block bitmap differences:  +(29360128--29360575) -61659136 -(61659139--61659140) -(61659142--61659143) -(79939743--79939747) -79943680 -79945728 -(79947776--79947959) -79951872 -(80097145--80097849)
Fix<y>? yes

Free blocks count wrong for group #0 (31223, counted=0).
Fix<y>? yes
.....
.....

/dev/sdc1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdc1: 41839/39075840 files (0.4% non-contiguous), 125969438/156282624 block

satimis@localhost:~$ 

```

Switched off the USB external enclosure and then switched it on again

The USB external enclosure was connected automatically.  However some newly saved files and directory have been deleted.

Is there anyway to recover them?

Besides:
This USB external enclosure and HD (Seagate SATA 640G) have been used for sometime.  I'm prepared replacing it with either an Exteral HD or NAS (1TB).  It is for home use.  Which device would you recommended?  TIA

satimis

---

