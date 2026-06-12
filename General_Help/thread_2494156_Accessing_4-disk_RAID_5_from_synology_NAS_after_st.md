---
title: "Accessing 4-disk RAID 5 from synology NAS after stupid mistake"
date: 2024-01-07
forum: General Help
---

### Post by ubuhitman on 2024-01-07
Hi, I tried to update my old synology NAS to an unsupported version of their OS (DiskStation manager) - yeah, I know. Couldn't get that reverted and I am out of support options, so the only option I saw was to recover my data by connecting the 4 disks to a clean Ubuntu install (v 23.10) using a Sabrent USB docking station. All drives can be separately accessed by the system and, as far as I know, don't have hardware problems.

The problem is, I cannot assemble the RAID 5 array, no matter what i try. I really hope that somebody can help me with this, because I'm really not an expert on this and out of options. I am a longtime user of iDrive and discovered that my synology only was back-upped intermittently.

What I tried:

**lsblk**
```

NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0  37.3G  0 disk 
&#9500;&#9472;sda1   8:1    0     1M  0 part 
&#9492;&#9472;sda2   8:2    0  37.3G  0 part /var/snap/firefox/common/host-hunspell
                                 /snap
                                 /
sdb      8:16   0   1.4T  0 disk 
&#9500;&#9472;sdb1   8:17   0   2.4G  0 part 
&#9500;&#9472;sdb2   8:18   0 509.9M  0 part 
&#9492;&#9472;sdb3   8:19   0   1.4T  0 part 
sdc      8:32   0   1.8T  0 disk 
&#9500;&#9472;sdc1   8:33   0   2.4G  0 part 
&#9500;&#9472;sdc2   8:34   0 509.9M  0 part 
&#9492;&#9472;sdc3   8:35   0   1.8T  0 part 
sdd      8:48   0   1.4T  0 disk 
&#9500;&#9472;sdd1   8:49   0   2.4G  0 part 
&#9500;&#9472;sdd2   8:50   0 509.9M  0 part 
&#9492;&#9472;sdd3   8:51   0   1.4T  0 part 
sde      8:64   0   1.4T  0 disk 
&#9500;&#9472;sde1   8:65   0   2.4G  0 part 
&#9500;&#9472;sde2   8:66   0 509.9M  0 part 
&#9492;&#9472;sde3   8:67   0   1.4T  0 part 
sdf      8:80   1     0B  0 disk 
sdg      8:96   1     0B  0 disk 
sdh      8:112  1     0B  0 disk 
sdi      8:128  1     0B  0 disk 

```

**mdadm --detail --scan **
```
empty
```

**cat /proc/mdstat**
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
unused devices: <none>

```

**ARRAY's I tried in the mdadm.conf file**
```

# ARRAY /dev/md0 level=raid5 num-devices=4 metadata=1.0 /dev/sdb3 /dev/sdc3 /dev/sdd3 /dev/sde3
# ARRAY /dev/md0 level=raid5 num-devices=4 metadata=1.0 UUID=b18d5178-16e5-38b3-2966-b0de212239d8

```

**fdisk -l /dev/sd***
[HTML]

Disk /dev/sda: 37.27 GiB, 40020664320 bytes, 78165360 sectors
Disk model: INTEL SSDSA2M040
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 6776138F-F71D-4E28-AC73-FC994BEE2273

Device     Start      End  Sectors  Size Type
/dev/sda1   2048     4095     2048    1M BIOS boot
/dev/sda2   4096 78161919 78157824 37.3G Linux filesystem


Disk /dev/sda1: 1 MiB, 1048576 bytes, 2048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sda2: 37.27 GiB, 40016805888 bytes, 78157824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/sdb: 1.36 TiB, 1500301910016 bytes, 2930277168 sectors
Disk model: ASM235CM        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xae700b00

Device     Boot   Start        End    Sectors   Size Id Type
/dev/sdb1            63    4980149    4980087   2.4G fd Linux raid autodetect
/dev/sdb2       4980150    6024374    1044225 509.9M fd Linux raid autodetect
/dev/sdb3       6281415 2930272064 2923990650   1.4T fd Linux raid autodetect


Disk /dev/sdb1: 2.37 GiB, 2549804544 bytes, 4980087 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes


Disk /dev/sdb2: 509.88 MiB, 534643200 bytes, 1044225 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes


Disk /dev/sdb3: 1.36 TiB, 1497083212800 bytes, 2923990650 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes


Disk /dev/sdc: 1.82 TiB, 2000398934016 bytes, 3907029168 sectors
Disk model: ASM235CM        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xdecc0900

Device     Boot   Start        End    Sectors   Size Id Type
/dev/sdc1            63    4980149    4980087   2.4G fd Linux raid autodetect
/dev/sdc2       4980150    6024374    1044225 509.9M fd Linux raid autodetect
/dev/sdc3       6281415 3907024064 3900742650   1.8T fd Linux raid autodetect

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.


Disk /dev/sdc1: 2.37 GiB, 2549804544 bytes, 4980087 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes


Disk /dev/sdc2: 509.88 MiB, 534643200 bytes, 1044225 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 1024 bytes


Disk /dev/sdc3: 1.82 TiB, 1997180236800 bytes, 3900742650 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes


Disk /dev/sdd: 1.36 TiB, 1500301910016 bytes, 2930277168 sectors
Disk model: ASM235CM        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes
Disklabel type: dos
Disk identifier: 0xc4b20400

Device     Boot   Start        End    Sectors   Size Id Type
/dev/sdd1            63    4980149    4980087   2.4G fd Linux raid autodetect
/dev/sdd2       4980150    6024374    1044225 509.9M fd Linux raid autodetect
/dev/sdd3       6281415 2930272064 2923990650   1.4T fd Linux raid autodetect


Disk /dev/sdd1: 2.37 GiB, 2549804544 bytes, 4980087 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes


Disk /dev/sdd2: 509.88 MiB, 534643200 bytes, 1044225 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes


Disk /dev/sdd3: 1.36 TiB, 1497083212800 bytes, 2923990650 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 33553920 bytes


Disk /dev/sde: 1.36 TiB, 1500301910016 bytes, 2930277168 sectors
Disk model: ASM235CM        
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0xa9560d00

Device     Boot   Start        End    Sectors   Size Id Type
/dev/sde1            63    4980149    4980087   2.4G fd Linux raid autodetect
/dev/sde2       4980150    6024374    1044225 509.9M fd Linux raid autodetect
/dev/sde3       6281415 2930272064 2923990650   1.4T fd Linux raid autodetect

Partition 1 does not start on physical sector boundary.
Partition 2 does not start on physical sector boundary.
Partition 3 does not start on physical sector boundary.


Disk /dev/sde1: 2.37 GiB, 2549804544 bytes, 4980087 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes


Disk /dev/sde2: 509.88 MiB, 534643200 bytes, 1044225 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 1024 bytes


Disk /dev/sde3: 1.36 TiB, 1497083212800 bytes, 2923990650 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Alignment offset: 512 bytes
fdisk: cannot open /dev/sdf: No medium found
fdisk: cannot open /dev/sdg: No medium found
fdisk: cannot open /dev/sdh: No medium found
fdisk: cannot open /dev/sdi: No medium found
[/HTML]**Also tried using R-Station and ReclaiMe in Windows with the following analysis**
```

This is a plain-text general description of the reconstructed array layout.

The array type is RAID5.
The array consists of 4 disks.

The disks are ordered as follows:
#00: Disk 2 - ASMT ASM235CM, Serial number 000519, \\.\PhysicalDrive2
#01: Disk 5 - ASMT ASM235CM, Serial number 000519, \\.\PhysicalDrive5
#02: Disk 4 - ASMT ASM235CM, Serial number 000519, \\.\PhysicalDrive4
#03: Disk 3 - ASMT ASM235CM, Serial number C000000519, \\.\PhysicalDrive3

Block size is 64,0 KB , same as 128 sectors.
The data starts at sector (LBA) 71 (this is often called "offset" or "start offset").

Block map is as follows: 

    1    2    3    P
    5    6    P    4
    9    P    7    8
    P  10  11  12

```

---

### Post by ubuhitman on 2024-01-11
So I've tried to recover some files (as if I had a corrupt drive) using Testdisk and could see a mess of files where some were recognizable. 

I tried the same with R-Studio, but after 3 days recovering, the result was the same. I'm feeling a bit defeated at the moment, so any help is much appreciated!

---

