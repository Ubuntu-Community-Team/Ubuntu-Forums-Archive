---
title: "Greater than expected Performance penalty of RAID1"
date: 2017-08-11
forum: General Help
---

### Post by bobnn on 2017-08-11
I seem to be suffering significant sequential write performance penalties, when writing to RAID1 ext3 partitions, as opposed to writing to "bare metal" ext3 partitions on the same disks in the same system.

I'd sure like some help with this, as the stats I've looked up don't seem to indicate that I should be suffering anything like this penalty.

All tests were of the form:
```
dd if=/dev/zero of=target  bs=1G count=4  oflag=dsync
```

When target was **/mnt/sdb4/test1.img/**, a bare-metal ext3 partition, the rate  was **181 MB/s**.




When the target was **a file on RAID1 device md1,** the rate was **142 MB/s**.
```
# mdadm -D /dev/md1
/dev/md1:
        Version : 1.0
  Creation Time : Mon Jul  3 12:01:27 2017
     Raid Level : raid1
     Array Size : 3838891896 (3661.05 GiB 3931.03 GB)
  Used Dev Size : 3838891896 (3661.05 GiB 3931.03 GB)
   Raid Devices : 2
  Total Devices : 2
    Persistence : Superblock is persistent

    Update Time : Fri Aug 11 09:52:31 2017
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           Name : srvr1:1  (local to host srvr1)
           UUID : fdbdfbc1:57d53064:9a2e1ca7:69527446
         Events : 82

    Number   Major   Minor   RaidDevice State
       0       8        5        0      active sync   /dev/sda5
       1       8       21        1      active sync   /dev/sdb5
[20170811-095236CDT root@srvr1:/root ]

```



**When the target was a file on RAID1 md0, the rate was _56.1 MB/s_.**

```
# mdadm -D /dev/md0
/dev/md0:
        Version : 0.90
  Creation Time : Mon Aug  1 18:42:48 2011
     Raid Level : raid1
     Array Size : 49702848 (47.40 GiB 50.90 GB)
  Used Dev Size : 49702848 (47.40 GiB 50.90 GB)
   Raid Devices : 2
  Total Devices : 2
Preferred Minor : 0
    Persistence : Superblock is persistent

    Update Time : Fri Aug 11 09:53:15 2017
          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

           UUID : 1f441a15:1ecc9254:4aeb3ab7:1778cbfa
         Events : 0.2207

    Number   Major   Minor   RaidDevice State
       0       8        3        0      active sync   /dev/sda3
       1       8       19        1      active sync   /dev/sdb3
[20170811-095329CDT root@srvr1:/root ]

```

The disks are the same make and model, 
```
# smartctl -i /dev/sda
smartctl 6.2 2013-07-26 r3841 [x86_64-linux-3.13.0-125-generic] (local build)
Copyright (C) 2002-13, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Device Model:     WDC WD4004FZWX-00GBGB0
Serial Number:    N8GEME8Y
LU WWN Device Id: 5 000cca 244c631c1
Firmware Version: 81.H0A81
User Capacity:    4,000,787,030,016 bytes [4.00 TB]
Sector Sizes:     512 bytes logical, 4096 bytes physical
Rotation Rate:    7200 rpm
Device is:        Not in smartctl database [for details use: -P showall]
ATA Version is:   ACS-2, ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 3.1, 6.0 Gb/s (current: 3.0 Gb/s)
Local Time is:    Fri Aug 11 10:12:59 2017 CDT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled



```

The partitioning of the disks is identical, with partitions aligned to 1MiB boundaries:
```
# gdisk -l /dev/sdb
GPT fdisk (gdisk) version 0.8.8

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sdb: 7814037168 sectors, 3.6 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): B5CE4CE2-DC99-4A90-807F-8F9FC303AC3A
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 7814037134
Partitions will be aligned on 2048-sector boundaries
Total free space is 58989 sectors (28.8 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1           20480           22527   1024.0 KiB  EF02  BIOS boot partition
   2           30720         1054719   500.0 MiB   EF00  EFI System
   3         1064960       103464959   48.8 GiB    FD00  Linux RAID
   4       103475200       136243199   15.6 GiB    8300  Linux filesystem
   5       136243200      7814027263   3.6 TiB     FD00  Linux RAID
```


I believe I've eliminated any commonality; as far as I can see the disks are using separate SATA controllers:

```
#lspci
...
00:1f.2 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 4 port SATA IDE Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
00:1f.5 IDE interface: Intel Corporation 6 Series/C200 Series Chipset Family 2 port SATA IDE Controller (rev 05)
0
.....
```

```
# udevadm info --query=path /dev/sda
/devices/pci0000:00/0000:00:1f.2/ata1/host0/target0:0:0/0:0:0:0/block/sda

```

```
# udevadm info --query=path /dev/sdb
/devices/pci0000:00/0000:00:1f.5/ata4/host3/target3:0:0/3:0:0:0/block/sdb

```

```
# uname -a
Linux srvr1 3.13.0-125-generic #174-Ubuntu SMP Mon Jul 10 18:51:24 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

```

---

