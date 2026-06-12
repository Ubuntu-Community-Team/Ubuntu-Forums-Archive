---
title: "set-up existing LDM stripe disk"
date: 2007-04-25
forum: General Help
---

### Post by manza on 2007-04-25
I want to set up two existing striped ntfs partitions on 3 disks.
Partitions is wizoff "dynamic disks"

I read documentation from [here]("http://www.mjmwired.net/kernel/Documentation/filesystems/ntfs.txt")
my ldminfo output is:

> Device: /dev/sdb

PRIVATE HEADER:
Version            : 2.11
Disk Id            : 88E0B66C-4F9F-4B5D-B0FE-6B35E97D4336
Logical disk start : 0x3F
Logical disk size  : 0x950E482 (76316 MB)
Configuration start: 0x950F0B0
Configuration size : 0x800 (1 MB)

TOC
Bitmap name        : "config"
Log bitmap start   : 0x11
Log bitmap size    : 0x5C9
Bitmap name        : "log"
Log bitmap start   : 0x5DA
Log bitmap size    : 0xE0
VMDB DATABASE HEADER:
Version            : 4/10
VBLK Size          : 0x80
Offset to VBLKs    : 0x200
Number of VBLKs    : 0x1720

VBLK DATABASE:
0x000000: <Component>
         Name        : Stripe2-01
         Object Id   : 0x042d
         Parent Id   : 0x042b
0x000000: <Component>
         Name        : Stripe1-01
         Object Id   : 0x041d
         Parent Id   : 0x041b
0x000000: <Partition>
         Name        : Disk3-01
         Object Id   : 0x0423
         Parent Id   : 0x041d
         Disk Id     : 0x0409
         Start       : 0x0
         Size        : 0x800000 (4096 MB)
         Volume Off  : 0x0 (0 MB)
0x000000: <Partition>
         Name        : Disk2-01
         Object Id   : 0x0421
         Parent Id   : 0x041d
         Disk Id     : 0x0406
         Start       : 0x0
         Size        : 0x800000 (4096 MB)
         Volume Off  : 0x0 (0 MB)
0x000000: <Partition>
         Name        : Disk3-02
         Object Id   : 0x0433
         Parent Id   : 0x042d
         Disk Id     : 0x0409
         Start       : 0x800000
         Size        : 0x8D0E400 (72220 MB)
         Volume Off  : 0x0 (0 MB)
0x000000: <Partition>
         Name        : Disk2-02
         Object Id   : 0x0431
         Parent Id   : 0x042d
         Disk Id     : 0x0406
         Start       : 0x800000
         Size        : 0x8D0E400 (72220 MB)
         Volume Off  : 0x0 (0 MB)
0x000000: <Partition>
         Name        : Disk1-01
         Object Id   : 0x041f
         Parent Id   : 0x041d
         Disk Id     : 0x0403
         Start       : 0x0
         Size        : 0x800000 (4096 MB)
         Volume Off  : 0x0 (0 MB)
0x000000: <Partition>
         Name        : Disk1-02
         Object Id   : 0x042f
         Parent Id   : 0x042d
         Disk Id     : 0x0403
         Start       : 0x800000
         Size        : 0x8D0E400 (72220 MB)
         Volume Off  : 0x0 (0 MB)
0x000000: <Disk>
         Name        : Disk3
         Object Id   : 0x0409
         Disk Id     : 9D70E598-2F52-4609-9B25-239C21D8D434
0x000000: <Disk>
         Name        : Disk2
         Object Id   : 0x0406
         Disk Id     : 2A3A3B55-C5AD-4C60-96BD-CE074B347E8E
0x000000: <Disk>
         Name        : Disk1
         Object Id   : 0x0403
         Disk Id     : 88E0B66C-4F9F-4B5D-B0FE-6B35E97D4336
0x000000: <DiskGroup>
         Name        : SfpDg0
         Object Id   : 0x0401
         GUID        : 
0x000000: <Volume>
         Name        : Stripe2
         Object Id   : 0x042b
         Volume state: ACTIVE
         Size        : 0x1A72AC00 (216661 MB)
         GUID        : 5490F492-54B0-48E3-A3C5-BD3A2F15AD0D
         Drive Hint  : E:
         Partition   : NTFS
0x000000: <Volume>
         Name        : Stripe1
         Object Id   : 0x041b
         Volume state: ACTIVE
         Size        : 0x01800000 (12288 MB)
         GUID        : ED0D6649-9D62-4511-A5DF-B854A530484C
         Drive Hint  : X:
         Partition   : NTFS

PARTITION LAYOUT:

Disk Disk3:
        Disk3-01 Offset: 0x00000000 Length: 0x00800000 (4096 MB)
        Disk3-02 Offset: 0x00800000 Length: 0x08D0E400 (72220 MB)
Disk Disk2:
        Disk2-01 Offset: 0x00000000 Length: 0x00800000 (4096 MB)
        Disk2-02 Offset: 0x00800000 Length: 0x08D0E400 (72220 MB)
Disk Disk1:
        Disk1-01 Offset: 0x00000000 Length: 0x00800000 (4096 MB)
        Disk1-02 Offset: 0x00800000 Length: 0x08D0E400 (72220 MB)

VOLUME DEFINITIONS:

Stripe2 Size: 0x1A72AC00 (216661 MB)
    Stripe2-01
      Disk3-02   VolumeOffset: 0x00000000 Offset: 0x00800000 Length: 0x08D0E400
      Disk2-02   VolumeOffset: 0x00000000 Offset: 0x00800000 Length: 0x08D0E400
      Disk1-02   VolumeOffset: 0x00000000 Offset: 0x00800000 Length: 0x08D0E400
Stripe1 Size: 0x01800000 (12288 MB)
    Stripe1-01
      Disk3-01   VolumeOffset: 0x00000000 Offset: 0x00000000 Length: 0x00800000
      Disk2-01   VolumeOffset: 0x00000000 Offset: 0x00000000 Length: 0x00800000
      Disk1-01   VolumeOffset: 0x00000000 Offset: 0x00000000 Length: 0x00800000



I create md0 & md1 devices with: 

sudo mdadm --create /dev/md0 --chunk=64 --level=0 --raid-devices=3 /dev/sdb1 /dev/sdc1 /dev/sdd1 

sudo mdadm --create /dev/md1 --chunk=64 --level=0 --raid-devices=3 /dev/sdb2 /dev/sdc2 /dev/sdd2 

Then mounted with ntfs-3g partition type. 

great!

---

