---
title: "GPT messed up, cant boot or access harddrive"
date: 2014-01-03
forum: General Help
---

### Post by gerwalt on 2014-01-03
Hi everyone,

I need a little help with a GPT Problem. First of all some information to my system:

I have a dual boot with Ubuntu 13.04 and Windows 7. I use Grub2 and GPT. I have currently 3 disks attached. The first is a SSD with BOOT, /, home for Ubuntu and a ntfs Partition for Windows.

And now the story:
Two or three days I had my iPod Nano attached to my PC while I was in Ubuntu. It was attached until yesterday, during that time I was as well in Windows as in Ubuntu. I think I detached it while I was on Ubuntu, but I'm not sure. I wanted to boot to Windows again, but it didnt boot anymore. Showed "Loading Files" bar and then got back to grub. But I could still boot Ubuntu.
I remembered that I had a similar problem, when I had an external drive attached to my PC and detached, and that I could repair it with "testdisk". So I started testdisk, used the analyze function and wrote the results without really reading them (stupid me). Now I have the problem, that when I boot the computer it wont even load Grub, just tries to start Windows where an error occurs (I can look up that one when I have finished this post). Currently I'm on a Live OS (Ubuntu 12.04.3) and I used gdisk and bootinfoscript to analyse the problem. It seems that my main disk is pretty messed up.

Output of fdisk seems pretty normal. sda is my SSD, sdb is another hdd with a ext4 and a ntfs partition, sdc is an external drive (that should only have 1tb space). sdd is the usb stick I'm using for the Live OS.

```
ubuntu@ubuntu:~$ sudo fdisk -l

Warnung: GPT (GUID-Partitionstabelle) auf '/dev/sda' erkannt! Das Hilfsprogramm Fdisk unterstützt GPT nicht. Verwenden Sie GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 Köpfe, 63 Sektoren/Spur, 15566 Zylinder, zusammen 250069680 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x00000000

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1               1      280581      140290+  ee  GPT
/dev/sda2        35215801    68770494    16777347   af  HFS / HFS+
/dev/sda3          280582     1304581      512000   83  Linux
/dev/sda4        16107048    16113221        3087    7  HPFS/NTFS/exFAT

Partitionstabelleneinträge sind nicht in Platten-Reihenfolge

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 Köpfe, 63 Sektoren/Spur, 60801 Zylinder, zusammen 976773168 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Festplattenidentifikation: 0x0009cbcd

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdb1   *        2048   689602552   344800252+   7  HPFS/NTFS/exFAT
/dev/sdb2       689604608   976773119   143584256   83  Linux

Disk /dev/sdc: 2199.0 GB, 2199023132672 bytes
255 Köpfe, 63 Sektoren/Spur, 267349 Zylinder, zusammen 4294967056 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x44fdfe06

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdc1              63  1953520064   976760001    7  HPFS/NTFS/exFAT

Platte /dev/sdd: 4127 MByte, 4127195136 Byte
255 Köpfe, 63 Sektoren/Spur, 501 Zylinder, zusammen 8060928 Sektoren
Einheiten = Sektoren von 1 × 512 = 512 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Festplattenidentifikation: 0x0217934c

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sdd1   *          63     8060927     4030432+   c  W95 FAT32 (LBA)
```

gdisk tells me that my GPT is corrupt and that I also have a MBR, which confuses me a little, dont know if that is caused by testdisk.

```
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 1
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 0AA2A1A4-7563-41FF-B850-B70F78838215
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 1-sector boundaries
Total free space is 215484745 sectors (102.8 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   2        35215801        68770494   16.0 GiB    AF00  Apple HFS/HFS+
   3          280582         1304581   500.0 MiB   8300  Linux filesystem
   4        16107048        16113221   3.0 MiB     0700  Microsoft basic data
ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Partition table scan:
  MBR: hybrid
  BSD: not present
  APM: not present
  GPT: damaged

Found valid MBR and corrupt GPT. Which do you want to use? (Using the
GPT MAY permit recovery of GPT data.)
 1 - MBR
 2 - GPT
 3 - Create blank GPT

Your answer: 2
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 4D0A8EB8-E281-6843-A722-79AFAD3C81E7
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 250069646
Partitions will be aligned on 1-sector boundaries
Total free space is 96813545 sectors (46.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   0700  
   2          280582         1304581   500.0 MiB   0700  
   3        13697667        13718405   10.1 MiB    0700  
   4        16107048        16113221   3.0 MiB     0700  
   5        35215801        68770494   16.0 GiB    AF00  
   6        76255608        76261781   3.0 MiB     0700  
   7        76261800        76267973   3.0 MiB     0700  
   8        76267992        76274165   3.0 MiB     0700  
   9        76277048        76279927   1.4 MiB     0700  
  10        97055432        97058311   1.4 MiB     0700  
  11        98621616        98624495   1.4 MiB     0700  
  12       117148623       117250065   49.5 MiB    AF00  
  13       118786047       237103102   56.4 GiB    0700
```

parted shows similar results

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit mb print
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? OK                                                             
Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 128036MB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start    End       Size     File system  Name  Flags
 1      1.05MB   106MB     105MB    fat32
 2      144MB    668MB     524MB    ext4
 3      7013MB   7024MB    10.6MB
 4      8247MB   8250MB    3.16MB   ntfs
 5      18030MB  35210MB   17180MB
 6      39043MB  39046MB   3.16MB   ntfs
 7      39046MB  39049MB   3.16MB   ntfs
 8      39049MB  39052MB   3.16MB   ntfs
 9      39054MB  39055MB   1.47MB
10      49692MB  49694MB   1.47MB
11      50494MB  50496MB   1.47MB
12      59980MB  60032MB   51.9MB
13      60818MB  121397MB  60578MB  ntfs
```

bootinfoscript shows a lot of errors for sda

```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img, but core.img can not be found at this 
    location.
 => No boot loader is installed in the MBR of /dev/sdb.
 => Windows is installed in the MBR of /dev/sdc.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /efi/Boot/bootx64.efi /efi/ubuntu/grubx64.efi

sda2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  FAT16
    Boot sector info:  According to the info in the boot sector, sda3 starts 
                       at sector 1. But according to the info from fdisk, 
                       sda3 starts at sector 13697667. According to the info 
                       in the boot sector, sda3 has 0 sectors.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda4 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda4 starts at sector 16107048.
    Operating System:  
    Boot files:        

sda5: __________________________________________________________________________

    File system:       hfs
    Boot sector type:  -
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda6: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda6 starts at sector 76255608.
    Operating System:  
    Boot files:        

sda7: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda7 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda7 starts at sector 76261800.
    Operating System:  
    Boot files:        

sda8: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  According to the info in the boot sector, sda8 starts 
                       at sector 2. But according to the info from fdisk, 
                       sda8 starts at sector 76267992.
    Operating System:  
    Boot files:        

sda9: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda9 starts 
                       at sector 0. But according to the info from fdisk, 
                       sda9 starts at sector 76277048. According to the info 
                       in the boot sector, sda9 has 0 sectors.
    Operating System:  
    Boot files:        

sda10: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda10 
                       starts at sector 0. But according to the info from 
                       fdisk, sda10 starts at sector 97055432. According to 
                       the info in the boot sector, sda10 has 0 sectors.
    Operating System:  
    Boot files:        

sda11: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sda11 
                       starts at sector 0. But according to the info from 
                       fdisk, sda11 starts at sector 98621616. According to 
                       the info in the boot sector, sda11 has 0 sectors.
    Operating System:  
    Boot files:        

sda12: _________________________________________________________________________

    File system:       hfs
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda12,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


sda13: _________________________________________________________________________

    File system:       
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info: 
    Mounting failed:   mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: wrong fs type, bad option, bad superblock on /dev/sda12,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdb2: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  
    Boot files:        

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sdd1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.07 2013-07-25
    Boot sector info:  Syslinux looks at sector 15784 of /dev/sdd1 for its 
                       second stage. SYSLINUX is installed in the /uui 
                       directory. The integrity check of the ADV area failed. 
                       According to the info in the boot sector, sdd1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdd1 starts at sector 63.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1       280,581       280,581  ee GPT
/dev/sda2          35,215,801    68,770,494    33,554,694  af HFS / HFS+
/dev/sda3             280,582     1,304,581     1,024,000  83 Linux
/dev/sda4          16,107,048    16,113,221         6,174   7 NTFS / exFAT / HPFS


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       206,847       204,800 Data partition (Windows/Linux)
/dev/sda2         280,582     1,304,581     1,024,000 Data partition (Windows/Linux)
/dev/sda3      13,697,667    13,718,405        20,739 Data partition (Windows/Linux)
/dev/sda4      16,107,048    16,113,221         6,174 Data partition (Windows/Linux)
/dev/sda5      35,215,801    68,770,494    33,554,694 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda6      76,255,608    76,261,781         6,174 Data partition (Windows/Linux)
/dev/sda7      76,261,800    76,267,973         6,174 Data partition (Windows/Linux)
/dev/sda8      76,267,992    76,274,165         6,174 Data partition (Windows/Linux)
/dev/sda9      76,277,048    76,279,927         2,880 Data partition (Windows/Linux)
/dev/sda10     97,055,432    97,058,311         2,880 Data partition (Windows/Linux)
/dev/sda11     98,621,616    98,624,495         2,880 Data partition (Windows/Linux)
/dev/sda12    117,148,623   117,250,065       101,443 Hierarchical File System Plus (HFS+) partition (Mac OS X)
/dev/sda13    118,786,047   237,103,102   118,317,056 Data partition (Windows/Linux)

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048   689,602,552   689,600,505   7 NTFS / exFAT / HPFS
/dev/sdb2         689,604,608   976,773,119   287,168,512  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 2199.0 GB, 2199023132672 bytes
255 heads, 63 sectors/track, 267349 cylinders, total 4294967056 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63 1,953,520,064 1,953,520,002   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 4127 MB, 4127195136 bytes
255 heads, 63 sectors/track, 501 cylinders, total 8060928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1    *             63     8,060,927     8,060,865   c W95 FAT32 (LBA)


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        887D-F3E4                              vfat       
/dev/sda10       1564-FBAC                              vfat       EFISECTOR
/dev/sda11       1564-FBAC                              vfat       EFISECTOR
/dev/sda12       c6d92ccf-b77f-3189-8fa4-bacceec65e31   hfs        O”
/dev/sda2        d7af4422-186a-4008-9bce-ceeb61c8c0cc   ext4       
/dev/sda3                                               vfat       
/dev/sda4        50D60A27D60A0DC2                       ntfs       Boot
/dev/sda5        acd7c1e0-4df7-36d7-8288-7c3bb2a9def0   hfs        
/dev/sda6        50D60A27D60A0DC2                       ntfs       Boot
/dev/sda7        50D60A27D60A0DC2                       ntfs       Boot
/dev/sda8        50D60A27D60A0DC2                       ntfs       Boot
/dev/sda9        7B46-E576                              vfat       EFISECTOR
/dev/sdb1        282CF48E2CF457F0                       ntfs       Games, Music and Data
/dev/sdb2        42b98e3c-9dfc-4439-b2be-943c7409ae00   ext4       data
/dev/sdc1        2A60950D6094E13D                       ntfs       My Book
/dev/sdd1        E1F5-5586                              vfat       UUI
/dev/sr0                                                iso9660    Fedora-17-i686-Live-Desktop.iso

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdd1        /cdrom                   vfat       (ro,noatime,fmask=0022,dmask=0022,codepage=437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda2

00000000  a4 81 00 00 50 10 27 00  ae d3 8b 50 ae d3 8b 50  |....P.'....P...P|
00000010  ae d3 8b 50 00 00 00 00  00 00 01 00 8a 13 00 00  |...P............|
00000020  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000030  00 00 00 00 00 00 00 00  c5 09 00 00 01 40 04 00  |.............@..|
00000040  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000060  00 00 00 00 ab 05 4e 9d  00 00 00 00 00 00 00 00  |......N.........|
00000070  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000080  a4 81 00 00 00 04 00 00  3e dd 8e 50 3e dd 8e 50  |........>..P>..P|
00000090  3e dd 8e 50 00 00 00 00  00 00 01 00 02 00 00 00  |>..P............|
000000a0  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
000000b0  00 00 00 00 00 00 00 00  01 00 00 00 01 2c 04 00  |.............,..|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  00 00 00 00 ac 05 4e 9d  00 00 00 00 00 00 00 00  |......N.........|
000000f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000100  a4 81 00 00 39 67 00 00  ae d3 8b 50 ae d3 8b 50  |....9g.....P...P|
00000110  ae d3 8b 50 00 00 00 00  00 00 01 00 34 00 00 00  |...P........4...|
00000120  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
00000130  00 00 00 00 00 00 00 00  1a 00 00 00 01 c8 00 00  |................|
00000140  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000160  00 00 00 00 ad 05 4e 9d  00 00 00 00 00 00 00 00  |......N.........|
00000170  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000180  a4 81 00 00 88 03 00 00  94 e5 8b 50 94 e5 8b 50  |...........P...P|
00000190  94 e5 8b 50 00 00 00 00  00 00 01 00 02 00 00 00  |...P............|
000001a0  00 00 08 00 01 00 00 00  0a f3 01 00 04 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  01 00 00 00 01 22 04 00  |............."..|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001e0  00 00 00 00 ce 5c 59 e4  00 00 00 00 00 00 00 00  |.....\Y.........|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000200

Unknown BootLoader on sda9

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 01 01 00  |.<.MSDOS5.0.....|
00000010  02 e0 00 40 0b f0 09 00  12 00 02 00 00 00 00 00  |...@............|
00000020  00 00 00 00 00 00 29 76  e5 46 7b 45 46 49 53 45  |......)v.F{EFISE|
00000030  43 54 4f 52 20 20 46 41  54 31 32 20 20 20 fa 33  |CTOR  FAT12   .3|
00000040  c0 8e d0 bc 00 7c 16 07  bb 78 00 36 c5 37 1e 56  |.....|...x.6.7.V|
00000050  16 53 bf 3e 7c b9 0b 00  fc f3 a4 06 1f c6 45 fe  |.S.>|.........E.|
00000060  0f 8b 0e 18 7c 88 4d f9  89 47 02 c7 07 3e 7c fb  |....|.M..G...>|.|
00000070  cd 13 72 79 33 c0 39 06  13 7c 74 08 8b 0e 13 7c  |..ry3.9..|t....||
00000080  89 0e 20 7c a0 10 7c f7  26 16 7c 03 06 1c 7c 13  |.. |..|.&.|...|.|
00000090  16 1e 7c 03 06 0e 7c 83  d2 00 a3 50 7c 89 16 52  |..|...|....P|..R|
000000a0  7c a3 49 7c 89 16 4b 7c  b8 20 00 f7 26 11 7c 8b  ||.I|..K|. ..&.|.|
000000b0  1e 0b 7c 03 c3 48 f7 f3  01 06 49 7c 83 16 4b 7c  |..|..H....I|..K||
000000c0  00 bb 00 05 8b 16 52 7c  a1 50 7c e8 92 00 72 1d  |......R|.P|...r.|
000000d0  b0 01 e8 ac 00 72 16 8b  fb b9 0b 00 be e6 7d f3  |.....r........}.|
000000e0  a6 75 0a 8d 7f 20 b9 0b  00 f3 a6 74 18 be 9e 7d  |.u... .....t...}|
000000f0  e8 5f 00 33 c0 cd 16 5e  1f 8f 04 8f 44 02 cd 19  |._.3...^....D...|
00000100  58 58 58 eb e8 8b 47 1a  48 48 8a 1e 0d 7c 32 ff  |XXX...G.HH...|2.|
00000110  f7 e3 03 06 49 7c 13 16  4b 7c bb 00 07 b9 03 00  |....I|..K|......|
00000120  50 52 51 e8 3a 00 72 d8  b0 01 e8 54 00 59 5a 58  |PRQ.:.r....T.YZX|
00000130  72 bb 05 01 00 83 d2 00  03 1e 0b 7c e2 e2 8a 2e  |r..........|....|
00000140  15 7c 8a 16 24 7c 8b 1e  49 7c a1 4b 7c ea 00 00  |.|..$|..I|.K|...|
00000150  70 00 ac 0a c0 74 29 b4  0e bb 07 00 cd 10 eb f2  |p....t).........|
00000160  3b 16 18 7c 73 19 f7 36  18 7c fe c2 88 16 4f 7c  |;..|s..6.|....O||
00000170  33 d2 f7 36 1a 7c 88 16  25 7c a3 4d 7c f8 c3 f9  |3..6.|..%|.M|...|
00000180  c3 b4 02 8b 16 4d 7c b1  06 d2 e6 0a 36 4f 7c 8b  |.....M|.....6O|.|
00000190  ca 86 e9 8a 16 24 7c 8a  36 25 7c cd 13 c3 0d 0a  |.....$|.6%|.....|
000001a0  4e 6f 6e 2d 53 79 73 74  65 6d 20 64 69 73 6b 20  |Non-System disk |
000001b0  6f 72 20 64 69 73 6b 20  65 72 72 6f 72 0d 0a 52  |or disk error..R|
000001c0  65 70 6c 61 63 65 20 61  6e 64 20 70 72 65 73 73  |eplace and press|
000001d0  20 61 6e 79 20 6b 65 79  20 77 68 65 6e 20 72 65  | any key when re|
000001e0  61 64 79 0d 0a 00 49 4f  20 20 20 20 20 20 53 59  |ady...IO      SY|
000001f0  53 4d 53 44 4f 53 20 20  20 53 59 53 00 00 55 aa  |SMSDOS   SYS..U.|
00000200

Unknown BootLoader on sda10

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 01 01 00  |.<.MSDOS5.0.....|
00000010  02 e0 00 40 0b f0 09 00  12 00 02 00 00 00 00 00  |...@............|
00000020  00 00 00 00 00 00 29 ac  fb 64 15 45 46 49 53 45  |......)..d.EFISE|
00000030  43 54 4f 52 20 20 46 41  54 31 32 20 20 20 fa 33  |CTOR  FAT12   .3|
00000040  c0 8e d0 bc 00 7c 16 07  bb 78 00 36 c5 37 1e 56  |.....|...x.6.7.V|
00000050  16 53 bf 3e 7c b9 0b 00  fc f3 a4 06 1f c6 45 fe  |.S.>|.........E.|
00000060  0f 8b 0e 18 7c 88 4d f9  89 47 02 c7 07 3e 7c fb  |....|.M..G...>|.|
00000070  cd 13 72 79 33 c0 39 06  13 7c 74 08 8b 0e 13 7c  |..ry3.9..|t....||
00000080  89 0e 20 7c a0 10 7c f7  26 16 7c 03 06 1c 7c 13  |.. |..|.&.|...|.|
00000090  16 1e 7c 03 06 0e 7c 83  d2 00 a3 50 7c 89 16 52  |..|...|....P|..R|
000000a0  7c a3 49 7c 89 16 4b 7c  b8 20 00 f7 26 11 7c 8b  ||.I|..K|. ..&.|.|
000000b0  1e 0b 7c 03 c3 48 f7 f3  01 06 49 7c 83 16 4b 7c  |..|..H....I|..K||
000000c0  00 bb 00 05 8b 16 52 7c  a1 50 7c e8 92 00 72 1d  |......R|.P|...r.|
000000d0  b0 01 e8 ac 00 72 16 8b  fb b9 0b 00 be e6 7d f3  |.....r........}.|
000000e0  a6 75 0a 8d 7f 20 b9 0b  00 f3 a6 74 18 be 9e 7d  |.u... .....t...}|
000000f0  e8 5f 00 33 c0 cd 16 5e  1f 8f 04 8f 44 02 cd 19  |._.3...^....D...|
00000100  58 58 58 eb e8 8b 47 1a  48 48 8a 1e 0d 7c 32 ff  |XXX...G.HH...|2.|
00000110  f7 e3 03 06 49 7c 13 16  4b 7c bb 00 07 b9 03 00  |....I|..K|......|
00000120  50 52 51 e8 3a 00 72 d8  b0 01 e8 54 00 59 5a 58  |PRQ.:.r....T.YZX|
00000130  72 bb 05 01 00 83 d2 00  03 1e 0b 7c e2 e2 8a 2e  |r..........|....|
00000140  15 7c 8a 16 24 7c 8b 1e  49 7c a1 4b 7c ea 00 00  |.|..$|..I|.K|...|
00000150  70 00 ac 0a c0 74 29 b4  0e bb 07 00 cd 10 eb f2  |p....t).........|
00000160  3b 16 18 7c 73 19 f7 36  18 7c fe c2 88 16 4f 7c  |;..|s..6.|....O||
00000170  33 d2 f7 36 1a 7c 88 16  25 7c a3 4d 7c f8 c3 f9  |3..6.|..%|.M|...|
00000180  c3 b4 02 8b 16 4d 7c b1  06 d2 e6 0a 36 4f 7c 8b  |.....M|.....6O|.|
00000190  ca 86 e9 8a 16 24 7c 8a  36 25 7c cd 13 c3 0d 0a  |.....$|.6%|.....|
000001a0  4e 6f 6e 2d 53 79 73 74  65 6d 20 64 69 73 6b 20  |Non-System disk |
000001b0  6f 72 20 64 69 73 6b 20  65 72 72 6f 72 0d 0a 52  |or disk error..R|
000001c0  65 70 6c 61 63 65 20 61  6e 64 20 70 72 65 73 73  |eplace and press|
000001d0  20 61 6e 79 20 6b 65 79  20 77 68 65 6e 20 72 65  | any key when re|
000001e0  61 64 79 0d 0a 00 49 4f  20 20 20 20 20 20 53 59  |ady...IO      SY|
000001f0  53 4d 53 44 4f 53 20 20  20 53 59 53 00 00 55 aa  |SMSDOS   SYS..U.|
00000200

Unknown BootLoader on sda11

00000000  eb 3c 90 4d 53 44 4f 53  35 2e 30 00 02 01 01 00  |.<.MSDOS5.0.....|
00000010  02 e0 00 40 0b f0 09 00  12 00 02 00 00 00 00 00  |...@............|
00000020  00 00 00 00 00 00 29 ac  fb 64 15 45 46 49 53 45  |......)..d.EFISE|
00000030  43 54 4f 52 20 20 46 41  54 31 32 20 20 20 fa 33  |CTOR  FAT12   .3|
00000040  c0 8e d0 bc 00 7c 16 07  bb 78 00 36 c5 37 1e 56  |.....|...x.6.7.V|
00000050  16 53 bf 3e 7c b9 0b 00  fc f3 a4 06 1f c6 45 fe  |.S.>|.........E.|
00000060  0f 8b 0e 18 7c 88 4d f9  89 47 02 c7 07 3e 7c fb  |....|.M..G...>|.|
00000070  cd 13 72 79 33 c0 39 06  13 7c 74 08 8b 0e 13 7c  |..ry3.9..|t....||
00000080  89 0e 20 7c a0 10 7c f7  26 16 7c 03 06 1c 7c 13  |.. |..|.&.|...|.|
00000090  16 1e 7c 03 06 0e 7c 83  d2 00 a3 50 7c 89 16 52  |..|...|....P|..R|
000000a0  7c a3 49 7c 89 16 4b 7c  b8 20 00 f7 26 11 7c 8b  ||.I|..K|. ..&.|.|
000000b0  1e 0b 7c 03 c3 48 f7 f3  01 06 49 7c 83 16 4b 7c  |..|..H....I|..K||
000000c0  00 bb 00 05 8b 16 52 7c  a1 50 7c e8 92 00 72 1d  |......R|.P|...r.|
000000d0  b0 01 e8 ac 00 72 16 8b  fb b9 0b 00 be e6 7d f3  |.....r........}.|
000000e0  a6 75 0a 8d 7f 20 b9 0b  00 f3 a6 74 18 be 9e 7d  |.u... .....t...}|
000000f0  e8 5f 00 33 c0 cd 16 5e  1f 8f 04 8f 44 02 cd 19  |._.3...^....D...|
00000100  58 58 58 eb e8 8b 47 1a  48 48 8a 1e 0d 7c 32 ff  |XXX...G.HH...|2.|
00000110  f7 e3 03 06 49 7c 13 16  4b 7c bb 00 07 b9 03 00  |....I|..K|......|
00000120  50 52 51 e8 3a 00 72 d8  b0 01 e8 54 00 59 5a 58  |PRQ.:.r....T.YZX|
00000130  72 bb 05 01 00 83 d2 00  03 1e 0b 7c e2 e2 8a 2e  |r..........|....|
00000140  15 7c 8a 16 24 7c 8b 1e  49 7c a1 4b 7c ea 00 00  |.|..$|..I|.K|...|
00000150  70 00 ac 0a c0 74 29 b4  0e bb 07 00 cd 10 eb f2  |p....t).........|
00000160  3b 16 18 7c 73 19 f7 36  18 7c fe c2 88 16 4f 7c  |;..|s..6.|....O||
00000170  33 d2 f7 36 1a 7c 88 16  25 7c a3 4d 7c f8 c3 f9  |3..6.|..%|.M|...|
00000180  c3 b4 02 8b 16 4d 7c b1  06 d2 e6 0a 36 4f 7c 8b  |.....M|.....6O|.|
00000190  ca 86 e9 8a 16 24 7c 8a  36 25 7c cd 13 c3 0d 0a  |.....$|.6%|.....|
000001a0  4e 6f 6e 2d 53 79 73 74  65 6d 20 64 69 73 6b 20  |Non-System disk |
000001b0  6f 72 20 64 69 73 6b 20  65 72 72 6f 72 0d 0a 52  |or disk error..R|
000001c0  65 70 6c 61 63 65 20 61  6e 64 20 70 72 65 73 73  |eplace and press|
000001d0  20 61 6e 79 20 6b 65 79  20 77 68 65 6e 20 72 65  | any key when re|
000001e0  61 64 79 0d 0a 00 49 4f  20 20 20 20 20 20 53 59  |ady...IO      SY|
000001f0  53 4d 53 44 4f 53 20 20  20 53 59 53 00 00 55 aa  |SMSDOS   SYS..U.|
00000200

Unknown BootLoader on sda12

00000000  54 41 49 4c 00 00 4d 4d  85 00 00 00 41 41 88 00  |TAIL..MM....AA..|
00000010  00 00 54 54 8b 00 00 00  45 45 8e 00 00 00 44 44  |..TT....EE....DD|
00000020  91 00 00 00 42 49 9b 00  00 00 00 00 00 00 00 00  |....BI..........|
00000030  00 00 00 00 a1 00 00 00  05 00 06 00 55 54 54 4f  |............UTTO|
00000040  4e 00 00 00 04 00 07 00  4d 41 47 45 00 00 0c 00  |N.......MAGE....|
00000050  08 00 50 46 52 41 4d 45  48 45 4c 50 45 52 00 00  |..PFRAMEHELPER..|
00000060  4f 55 b8 00 00 00 00 00  c1 00 00 00 00 00 fc 00  |OU..............|
00000070  00 00 0b 00 8c 00 4f 4c  45 41 4e 43 48 4f 49 43  |......OLEANCHOIC|
00000080  45 00 00 00 45 45 c4 00  00 00 41 41 c7 00 00 00  |E...EE....AA....|
00000090  44 44 ca 00 00 00 43 43  cd 00 00 00 52 52 d0 00  |DD....CC....RR..|
000000a0  00 00 55 55 d3 00 00 00  4d 4d d6 00 00 00 42 42  |..UU....MM....BB|
000000b0  d9 00 00 00 42 42 dc 00  00 00 41 55 f3 00 00 00  |....BB....AU....|
000000c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000000e0  00 00 00 00 f7 00 00 00  01 00 09 00 52 00 00 00  |............R...|
000000f0  04 00 0a 00 54 54 4f 4e  00 00 04 00 0b 00 54 54  |....TTON......TT|
00000100  4f 4e 00 00 41 55 18 01  00 00 00 00 00 00 00 00  |ON..AU..........|
00000110  00 00 00 00 1e 01 00 00  00 00 00 00 00 00 00 00  |................|
00000120  00 00 3b 01 00 00 00 00  00 00 00 00 00 00 a3 01  |..;.............|
00000130  00 00 06 00 8d 00 54 45  47 4f 52 59 00 00 45 55  |......TEGORY..EU|
00000140  31 01 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |1...............|
00000150  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000160  37 01 00 00 05 00 0c 00  43 4b 42 4f 58 00 00 00  |7.......CKBOX...|
00000170  02 00 0d 00 4e 4b 00 00  4c 4e 40 01 89 01 9e 01  |....NK..LN@.....|
00000180  00 00 4f 4f 43 01 00 00  52 52 46 01 00 00 41 53  |..OOC...RRF...AS|
00000190  5b 01 00 00 00 00 79 01  00 00 00 00 00 00 00 00  |[.....y.........|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 80 01 00 00  52 52 5e 01 00 00 45 45  |........RR^...EE|
000001c0  61 01 00 00 41 41 64 01  00 00 42 49 6e 01 00 00  |a...AAd...BIn...|
000001d0  00 00 00 00 00 00 00 00  00 00 74 01 00 00 05 00  |..........t.....|
000001e0  0e 00 55 54 54 4f 4e 00  00 00 04 00 0f 00 4d 41  |..UTTON.......MA|
000001f0  47 45 00 00 07 00 10 00  52 4f 50 44 4f 57 4e 00  |GE......ROPDOWN.|
00000200


=============================== StdErr Messages: ===============================

ERROR: asr: reading /dev/sdc[Input/output error]
ERROR: ddf1: reading /dev/sdc[Input/output error]
ERROR: ddf1: reading /dev/sdc[Input/output error]
ERROR: hpt45x: reading /dev/sdc[Input/output error]
ERROR: isw: reading /dev/sdc[Input/output error]
ERROR: isw: reading /dev/sdc[Input/output error]
ERROR: isw: reading /dev/sdc[Input/output error]
ERROR: jmicron: reading /dev/sdc[Input/output error]
ERROR: lsi: reading /dev/sdc[Input/output error]
ERROR: nvidia: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: sil: reading /dev/sdc[Input/output error]
ERROR: via: reading /dev/sdc[Input/output error]
ERROR: asr: reading /dev/sdc[Input/output error]
ERROR: ddf1: reading /dev/sdc[Input/output error]
ERROR: ddf1: reading /dev/sdc[Input/output error]
ERROR: hpt45x: reading /dev/sdc[Input/output error]
ERROR: isw: reading /dev/sdc[Input/output error]
ERROR: isw: reading /dev/sdc[Input/output error]
ERROR: isw: reading /dev/sdc[Input/output error]
ERROR: jmicron: reading /dev/sdc[Input/output error]
ERROR: lsi: reading /dev/sdc[Input/output error]
ERROR: nvidia: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: pdc: reading /dev/sdc[Input/output error]
ERROR: sil: reading /dev/sdc[Input/output error]
ERROR: via: reading /dev/sdc[Input/output error]
hexdump: sda3/_[^??ÉÉÉ: Input/output error
hexdump: sda3/_[^??ÉÉÉ: Input/output error
hexdump: sda3/_[^??ÉÉÉ: Input/output error
hexdump: sda3/???  ä?.äù: Input/output error
hexdump: sda3/???  ä?.äù: Input/output error
hexdump: sda3/???  ä?.äù: Input/output error
hexdump: sda3/?.  : Input/output error
hexdump: sda3/?.  : Input/output error
hexdump: sda3/?.  : Input/output error
hexdump: sda3/?".: Input/output error
hexdump: sda3/?".: Input/output error
hexdump: sda3/?".: Input/output error
hexdump: sda3/?@?ÉÉÉÉÉ: Input/output error
hexdump: sda3/?@?ÉÉÉÉÉ: Input/output error
hexdump: sda3/?@?ÉÉÉÉÉ: Input/output error
hexdump: sda3/?Å?  ï??.: Input/output error
hexdump: sda3/?Å?  ï??.: Input/output error
hexdump: sda3/?Å?  ï??.: Input/output error
hexdump: sda3/?ìäá.: Input/output error
hexdump: sda3/?ìäá.: Input/output error
hexdump: sda3/?ìäá.: Input/output error
hexdump: sda3/: Input/output error
hexdump: sda3/: Input/output error
hexdump: sda3/: Input/output error
hexdump: sda3/à?.à÷: Input/output error
hexdump: sda3/à?.à÷: Input/output error
hexdump: sda3/à?.à÷: Input/output error
hexdump: sda3/â}: Input/output error
hexdump: sda3/â}: Input/output error
hexdump: sda3/â}: Input/output error
hexdump: sda3/  ä?ä?: Input/output error
hexdump: sda3/  ä?ä?: Input/output error
hexdump: sda3/  ä?ä?: Input/output error
hexdump: sda3/? .^?: Input/output error
hexdump: sda3/? .^?: Input/output error
hexdump: sda3/? .^?: Input/output error
hexdump: sda3/ï??ê?  .ä?: Input/output error
hexdump: sda3/ï??ê?  .ä?: Input/output error
hexdump: sda3/ï??ê?  .ä?: Input/output error
hexdump: sda3/ï±â~4.ïF0: Input/output error
hexdump: sda3/ï±â~4.ïF0: Input/output error
hexdump: sda3/ï±â~4.ïF0: Input/output error
hexdump: sda3/9]|cï?é: Input/output error
hexdump: sda3/9]|cï?é: Input/output error
hexdump: sda3/9]|cï?é: Input/output error
hexdump: sda3/ÉÉÉèA]¿.à?: Input/output error
hexdump: sda3/ÉÉÉèA]¿.à?: Input/output error
hexdump: sda3/ÉÉÉèA]¿.à?: Input/output error
hexdump: sda3/ïA?ÉÉÉÉ: Input/output error
hexdump: sda3/ïA?ÉÉÉÉ: Input/output error
hexdump: sda3/ïA?ÉÉÉÉ: Input/output error
hexdump: sda3/ÉÉ?A?à.e: Input/output error
hexdump: sda3/ÉÉ?A?à.e: Input/output error
hexdump: sda3/ÉÉ?A?à.e: Input/output error
hexdump: sda3/+ºîAÄ±^.#by: Input/output error
hexdump: sda3/+ºîAÄ±^.#by: Input/output error
hexdump: sda3/+ºîAÄ±^.#by: Input/output error
hexdump: sda3/#?  ä?à.&b: Input/output error
hexdump: sda3/#?  ä?à.&b: Input/output error
hexdump: sda3/#?  ä?à.&b: Input/output error
hexdump: sda3/ï??e??.?÷?: Input/output error
hexdump: sda3/ï??e??.?÷?: Input/output error
hexdump: sda3/ï??e??.?÷?: Input/output error
hexdump: sda3/ï?à?î.?e: Input/output error
hexdump: sda3/ï?à?î.?e: Input/output error
hexdump: sda3/ï?à?î.?e: Input/output error
hexdump: sda3/ïï?ëe??.:: Input/output error
hexdump: sda3/ïï?ëe??.:: Input/output error
hexdump: sda3/ïï?ëe??.:: Input/output error
hexdump: sda3/?e°3??_.^[?: Input/output error
hexdump: sda3/?e°3??_.^[?: Input/output error
hexdump: sda3/?e°3??_.^[?: Input/output error
hexdump: sda3/ï?ïE?E. u: Input/output error
hexdump: sda3/ï?ïE?E. u: Input/output error
hexdump: sda3/ï?ïE?E. u: Input/output error
hexdump: sda3/ïe.?I: Input/output error
hexdump: sda3/ïe.?I: Input/output error
hexdump: sda3/ïe.?I: Input/output error
hexdump: sda3/ï?ïEVï±.ëà: Input/output error
hexdump: sda3/ï?ïEVï±.ëà: Input/output error
hexdump: sda3/ï?ïEVï±.ëà: Input/output error
hexdump: sda3/ï??E?Y.]?: Input/output error
hexdump: sda3/ï??E?Y.]?: Input/output error
hexdump: sda3/ï??E?Y.]?: Input/output error
hexdump: sda3/????èF0.?^P: Input/output error
hexdump: sda3/????èF0.?^P: Input/output error
hexdump: sda3/????èF0.?^P: Input/output error
hexdump: sda3/äFW.]?: Input/output error
hexdump: sda3/äFW.]?: Input/output error
hexdump: sda3/äFW.]?: Input/output error
hexdump: sda3/à,g.]?: Input/output error
hexdump: sda3/à,g.]?: Input/output error
hexdump: sda3/à,g.]?: Input/output error
hexdump: sda3/. h|: Input/output error
hexdump: sda3/. h|: Input/output error
hexdump: sda3/. h|: Input/output error
hexdump: sda3/ïh?. ]: Input/output error
hexdump: sda3/ïh?. ]: Input/output error
hexdump: sda3/ïh?. ]: Input/output error
hexdump: sda3/i.àj: Input/output error
hexdump: sda3/i.àj: Input/output error
hexdump: sda3/i.àj: Input/output error
hexdump: sda3/ion.dll.Dll: Input/output error
hexdump: sda3/ion.dll.Dll: Input/output error
hexdump: sda3/ion.dll.Dll: Input/output error
hexdump: sda3/ÉÉÉïIà?.t ?: Input/output error
hexdump: sda3/ÉÉÉïIà?.t ?: Input/output error
hexdump: sda3/ÉÉÉïIà?.t ?: Input/output error
hexdump: sda3/ivïqä.ä: Input/output error
hexdump: sda3/ivïqä.ä: Input/output error
hexdump: sda3/ivïqä.ä: Input/output error
hexdump: sda3/???  ä?.à]j: Input/output error
hexdump: sda3/???  ä?.à]j: Input/output error
hexdump: sda3/???  ä?.à]j: Input/output error
hexdump: sda3/?k?  ä?.àG[: Input/output error
hexdump: sda3/?k?  ä?.àG[: Input/output error
hexdump: sda3/?k?  ä?.àG[: Input/output error
hexdump: sda3/ïkpwâ??.: Input/output error
hexdump: sda3/ïkpwâ??.: Input/output error
hexdump: sda3/ïkpwâ??.: Input/output error
hexdump: sda3/??.Éâl: Input/output error
hexdump: sda3/??.Éâl: Input/output error
hexdump: sda3/??.Éâl: Input/output error
hexdump: sda3/??  ä?.àm\: Input/output error
hexdump: sda3/??  ä?.àm\: Input/output error
hexdump: sda3/??  ä?.àm\: Input/output error
hexdump: sda3/ìM? 7?.?  : Input/output error
hexdump: sda3/ìM? 7?.?  : Input/output error
hexdump: sda3/ìM? 7?.?  : Input/output error
hexdump: sda3/(ïïmï@.ëA: Input/output error
hexdump: sda3/(ïïmï@.ëA: Input/output error
hexdump: sda3/(ïïmï@.ëA: Input/output error
hexdump: sda3/ìM u???.?  : Input/output error
hexdump: sda3/ìM u???.?  : Input/output error
hexdump: sda3/ìM u???.?  : Input/output error
hexdump: sda3/m? u?d: Input/output error
hexdump: sda3/m? u?d: Input/output error
hexdump: sda3/m? u?d: Input/output error
hexdump: sda3/±ïn0v?!: Input/output error
hexdump: sda3/±ïn0v?!: Input/output error
hexdump: sda3/±ïn0v?!: Input/output error
hexdump: sda3/?âß?ïN.X??: Input/output error
hexdump: sda3/?âß?ïN.X??: Input/output error
hexdump: sda3/?âß?ïN.X??: Input/output error
hexdump: sda3/à?P.â=,: Input/output error
hexdump: sda3/à?P.â=,: Input/output error
hexdump: sda3/à?P.â=,: Input/output error
hexdump: sda3/P???  ë~._^: Input/output error
hexdump: sda3/P???  ë~._^: Input/output error
hexdump: sda3/P???  ë~._^: Input/output error
hexdump: sda3/ë~P?3?  .wìf: Input/output error
hexdump: sda3/ë~P?3?  .wìf: Input/output error
hexdump: sda3/ë~P?3?  .wìf: Input/output error
hexdump: sda3/ìà??  Pj: Input/output error
hexdump: sda3/ìà??  Pj: Input/output error
hexdump: sda3/ìà??  Pj: Input/output error
hexdump: sda3/^pï?á.à t: Input/output error
hexdump: sda3/^pï?á.à t: Input/output error
hexdump: sda3/^pï?á.à t: Input/output error
hexdump: sda3/ ?]°q?e.Q?: Input/output error
hexdump: sda3/ ?]°q?e.Q?: Input/output error
hexdump: sda3/ ?]°q?e.Q?: Input/output error
hexdump: sda3/ëïqëp.ëa: Input/output error
hexdump: sda3/ëïqëp.ëa: Input/output error
hexdump: sda3/ëïqëp.ëa: Input/output error
hexdump: sda3/R.ä? : Input/output error
hexdump: sda3/R.ä? : Input/output error
hexdump: sda3/R.ä? : Input/output error
hexdump: sda3/sï??(?  .ä?: Input/output error
hexdump: sda3/sï??(?  .ä?: Input/output error
hexdump: sda3/sï??(?  .ä?: Input/output error
hexdump: sda3/SVWì??: Input/output error
hexdump: sda3/SVWì??: Input/output error
hexdump: sda3/SVWì??: Input/output error
hexdump: sda3/±?.t: Input/output error
hexdump: sda3/±?.t: Input/output error
hexdump: sda3/±?.t: Input/output error
hexdump: sda3/ï?á.t3ì: Input/output error
hexdump: sda3/ï?á.t3ì: Input/output error
hexdump: sda3/ï?á.t3ì: Input/output error
hexdump: sda3/?t%ìHï.;?: Input/output error
hexdump: sda3/?t%ìHï.;?: Input/output error
hexdump: sda3/?t%ìHï.;?: Input/output error
hexdump: sda3/à?tïq .p3: Input/output error
hexdump: sda3/à?tïq .p3: Input/output error
hexdump: sda3/à?tïq .p3: Input/output error
hexdump: sda3/àæt?u '.?u : Input/output error
hexdump: sda3/àæt?u '.?u : Input/output error
hexdump: sda3/àæt?u '.?u : Input/output error
hexdump: sda3/???  ä?.à?u: Input/output error
hexdump: sda3/???  ä?.à?u: Input/output error
hexdump: sda3/???  ä?.à?u: Input/output error
hexdump: sda3/?.?u: Input/output error
hexdump: sda3/?.?u: Input/output error
hexdump: sda3/?.?u: Input/output error
hexdump: sda3/à#.à?u: Input/output error
hexdump: sda3/à#.à?u: Input/output error
hexdump: sda3/à#.à?u: Input/output error
hexdump: sda3/ à?u1ï~.à : Input/output error
hexdump: sda3/ à?u1ï~.à : Input/output error
hexdump: sda3/ à?u1ï~.à : Input/output error
hexdump: sda3/;uë1^;.A: Input/output error
hexdump: sda3/;uë1^;.A: Input/output error
hexdump: sda3/;uë1^;.A: Input/output error
hexdump: sda3/ï Uï?â?.âe°: Input/output error
hexdump: sda3/ï Uï?â?.âe°: Input/output error
hexdump: sda3/ï Uï?â?.âe°: Input/output error
hexdump: sda3/ï uï?ïe.âx: Input/output error
hexdump: sda3/ï uï?ïe.âx: Input/output error
hexdump: sda3/ï uï?ïe.âx: Input/output error
hexdump: sda3/ uï?â?h.: Input/output error
hexdump: sda3/ uï?â?h.: Input/output error
hexdump: sda3/ uï?â?h.: Input/output error
hexdump: sda3/ïuìN???.?  : Input/output error
hexdump: sda3/ïuìN???.?  : Input/output error
hexdump: sda3/ïuìN???.?  : Input/output error
hexdump: sda3/ïuìN??b.?  : Input/output error
hexdump: sda3/ïuìN??b.?  : Input/output error
hexdump: sda3/ïuìN??b.?  : Input/output error
hexdump: sda3/ééï uï?ï.Q`ï: Input/output error
hexdump: sda3/ééï uï?ï.Q`ï: Input/output error
hexdump: sda3/ééï uï?ï.Q`ï: Input/output error
hexdump: sda3/ééï uï?ï.Qï: Input/output error
hexdump: sda3/ééï uï?ï.Qï: Input/output error
hexdump: sda3/ééï uï?ï.Qï: Input/output error
hexdump: sda3/ï Uï?QQV.ï±÷: Input/output error
hexdump: sda3/ï Uï?QQV.ï±÷: Input/output error
hexdump: sda3/ï Uï?QQV.ï±÷: Input/output error
hexdump: sda3/ï Uï?Sï].s?: Input/output error
hexdump: sda3/ï Uï?Sï].s?: Input/output error
hexdump: sda3/ï Uï?Sï].s?: Input/output error
hexdump: sda3/]? u? u?.?: Input/output error
hexdump: sda3/]? u? u?.?: Input/output error
hexdump: sda3/]? u? u?.?: Input/output error
hexdump: sda3/ééï uï? .uï: Input/output error
hexdump: sda3/ééï uï? .uï: Input/output error
hexdump: sda3/ééï uï? .uï: Input/output error
hexdump: sda3/?u?'ëu '.? l: Input/output error
hexdump: sda3/?u?'ëu '.? l: Input/output error
hexdump: sda3/?u?'ëu '.? l: Input/output error
hexdump: sda3/uw?ï??: Input/output error
hexdump: sda3/uw?ï??: Input/output error
hexdump: sda3/uw?ï??: Input/output error
hexdump: sda3/²  à?|# .v?: Input/output error
hexdump: sda3/²  à?|# .v?: Input/output error
hexdump: sda3/²  à?|# .v?: Input/output error
hexdump: sda3/?v8?v@?e.?^: Input/output error
hexdump: sda3/?v8?v@?e.?^: Input/output error
hexdump: sda3/?v8?v@?e.?^: Input/output error
hexdump: sda3/ï?â?vï±.÷F\: Input/output error
hexdump: sda3/ï?â?vï±.÷F\: Input/output error
hexdump: sda3/ï?â?vï±.÷F\: Input/output error
hexdump: sda3/ïv??^?ì.M??: Input/output error
hexdump: sda3/ïv??^?ì.M??: Input/output error
hexdump: sda3/ïv??^?ì.M??: Input/output error
hexdump: sda3/w._ä: Input/output error
hexdump: sda3/w._ä: Input/output error
hexdump: sda3/w._ä: Input/output error
hexdump: sda3/W Pïà?.àD: Input/output error
hexdump: sda3/W Pïà?.àD: Input/output error
hexdump: sda3/W Pïà?.àD: Input/output error
hexdump: sda3/;?wï?;?.wï: Input/output error
hexdump: sda3/;?wï?;?.wï: Input/output error
hexdump: sda3/;?wï?;?.wï: Input/output error
hexdump: sda3/??ª.xï: Input/output error
hexdump: sda3/??ª.xï: Input/output error
hexdump: sda3/??ª.xï: Input/output error
hexdump: sda3/?²?  Yï?.^]?: Input/output error
hexdump: sda3/?²?  Yï?.^]?: Input/output error
hexdump: sda3/?²?  Yï?.^]?: Input/output error
hexdump: sda3/z?  ëb?.6!: Input/output error
hexdump: sda3/z?  ëb?.6!: Input/output error
hexdump: sda3/z?  ëb?.6!: Input/output error
./bootinfoscript: line 1646: [: 2.73495e+09: integer expression expected
```

Is there any way I can undo my mistake and repair the GPT or do I have to reinstall my system?

If you need further information, just tell me.

---

### Post by gerwalt on 2014-01-03
To secure my data I tried to mount the partitions containing the OS, but got an error that looks the same for each partition:

```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda12,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

E.g. the sda12 output of dmesg:

```
[20905.004937] hfs: unable to locate alternate MDB
[20905.004941] hfs: continuing without an alternate MDB
[20905.005483] attempt to access beyond end of device
[20905.005487] sda12: rw=0, want=108914, limit=101443
[20905.005490] quiet_error: 3 callbacks suppressed
[20905.005492] Buffer I/O error on device sda12, logical block 108913
[20905.005496] attempt to access beyond end of device
[20905.005498] sda12: rw=0, want=108915, limit=101443
[20905.005500] Buffer I/O error on device sda12, logical block 108914
[20905.005502] attempt to access beyond end of device
[20905.005504] sda12: rw=0, want=108916, limit=101443
[20905.005506] Buffer I/O error on device sda12, logical block 108915
[20905.005508] attempt to access beyond end of device
[20905.005510] sda12: rw=0, want=108917, limit=101443
[20905.005512] Buffer I/O error on device sda12, logical block 108916
[20905.005514] attempt to access beyond end of device
[20905.005516] sda12: rw=0, want=108918, limit=101443
[20905.005518] Buffer I/O error on device sda12, logical block 108917
[20905.005520] attempt to access beyond end of device
[20905.005522] sda12: rw=0, want=108919, limit=101443
[20905.005524] Buffer I/O error on device sda12, logical block 108918
[20905.005525] attempt to access beyond end of device
[20905.005527] sda12: rw=0, want=108920, limit=101443
[20905.005529] Buffer I/O error on device sda12, logical block 108919
[20905.005531] attempt to access beyond end of device
[20905.005533] sda12: rw=0, want=108921, limit=101443
[20905.005535] Buffer I/O error on device sda12, logical block 108920
[20905.005538] attempt to access beyond end of device
[20905.005540] sda12: rw=0, want=108914, limit=101443
[20905.005542] Buffer I/O error on device sda12, logical block 108913
[20905.005544] attempt to access beyond end of device
[20905.005546] sda12: rw=0, want=108915, limit=101443
[20905.005547] Buffer I/O error on device sda12, logical block 108914
[20905.005549] attempt to access beyond end of device
[20905.005551] sda12: rw=0, want=108916, limit=101443
[20905.005553] attempt to access beyond end of device
[20905.005555] sda12: rw=0, want=108917, limit=101443
[20905.005557] attempt to access beyond end of device
[20905.005559] sda12: rw=0, want=108918, limit=101443
[20905.005561] attempt to access beyond end of device
[20905.005563] sda12: rw=0, want=108919, limit=101443
[20905.005565] attempt to access beyond end of device
[20905.005567] sda12: rw=0, want=108920, limit=101443
[20905.005569] attempt to access beyond end of device
[20905.005571] sda12: rw=0, want=108921, limit=101443
[20905.005582] hfs: unable to open extent tree
[20905.005585] hfs: can't find a HFS filesystem on dev sda12.
```

I can only access the 3 EFISECTORs which are sda9 to sda11 and 4 Boot Partitions which are sda4 to sda8, as well as the original Boot Partition sda1. Except the original boot partition all of these are really small (less than 1MB).

If I cant repair the mess with GPT, is there at least any way to access my data and secure what I havent backed up?

---

### Post by gerwalt on 2014-01-03
Is here anyone who can help me restore the gpt like "YesWeCan" told "Quaxo76" in this post: [http://ubuntuforums.org/showthread.php?t=1849060](http://ubuntuforums.org/showthread.php?t=1849060)

It seemed to be about MBR and ext3 mostly (I use GPT and ext4 and ntfs mostly), so I probably cant use the same commands.

---

### Post by gerwalt on 2014-01-03
Results of testdisk after analysing:

```
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63

The harddisk (128 GB / 119 GiB) seems too small! (< 1331 GB / 1240 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Mac HFS                  1965219 2600910116 2598944898
   Mac HFS                  3066614  765480213  762413600
   Mac HFS                239453227 1353303851 1113850625 [D^B]
```

Structure found by testdisk:

```
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63
     Partition               Start        End    Size in sectors
>P MS Data                     2048     206847     204800 [NO NAME]
 P MS Data                   280582    1304581    1024000
 P MS Data                 13697667   13718405      20739 [NO NAME]
 P MS Data                 16107048   16113221       6174 [Boot]
 P Mac HFS                 35215801   68770494   33554694
 P MS Data                 76255608   76261781       6174 [Boot]
 P MS Data                 76261800   76267973       6174 [Boot]
 P MS Data                 76267992   76274165       6174 [Boot]
 P MS Data                 76277048   76279927       2880 [EFISECTOR]
 P MS Data                 97055432   97058311       2880 [EFISECTOR]
 P MS Data                 98621616   98624495       2880 [EFISECTOR]
 P Mac HFS                117148623  117250065     101443 [O~T^B]
 P MS Data                118786047  237103102  118317056
```

---

### Post by YesWeCan on 2014-01-03
Hi. Well it seems to me that you have inadvertently mangled the partition table of your disk. It doesn't look
good but it may be possible to do a manual reconstruction of the partition table.

First, I would like to know what partitions you think you had on the SSD before the incident and roughly how
big they were?
[FONT=courier new][FONT=arial]
[/FONT]
[/FONT]

---

### Post by gerwalt on 2014-01-04
I had a / with 500MB, /boot for EFI with 100MB. Those seem to be still there at the beginning of the drive. Both ext4. For Windows I had a NTFS Partition with around 60GB and /home with I think 30gb, also ext4. I'm not sure, but I also had some unallocated space, around 10-20GB.

---

### Post by YesWeCan on 2014-01-04
The challenge is to try to find where the original partitions started and ended. The only one that seems known is the 500MB linux.
Can you run testdisk on sda again and do a "deep search"?
See: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#A_partition_is_still_missing:_Deeper_Search)

---

### Post by gerwalt on 2014-01-04
Yes, already did that, but currently dont have the results. There were like 500 Partitions. Let me do the deep search again and then I'll try to post the result here.

And I think I have to correct my numbers to the partitions. I still think that there were a 500mb and a 100mb partition, but I forgot swap and I'm sure / was bigger than just 500mb. swap must have been about 16gb (same as my ram size) and / probably 10gb. the 100mb was for EFI and 500 maybe for /boot. /home was maybe like 20gb.

So many maybes I hope that at least something is correct. :(

---

### Post by gerwalt on 2014-01-04
Partitions that testdisk cant recover after quick search:

```
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63

The harddisk (128 GB / 119 GiB) seems too small! (< 1331 GB / 1240 GiB)
Check the harddisk size: HD jumpers settings, BIOS detection...

The following partitions can't be recovered:
     Partition               Start        End    Size in sectors
>  Mac HFS                  1965219 2600910116 2598944898
   Mac HFS                  3066614  765480213  762413600
   Mac HFS                239453227 1353303851 1113850625 [D^B]
```

Structure after Quick Search:

```
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63
     Partition               Start        End    Size in sectors
>P MS Data                     2048     206847     204800 [NO NAME]
 P MS Data                   280582    1304581    1024000
 P MS Data                 13697667   13718405      20739 [NO NAME]
 P MS Data                 16107048   16113221       6174 [Boot]
 P Mac HFS                 35215801   68770494   33554694
 P MS Data                 76255608   76261781       6174 [Boot]
 P MS Data                 76261800   76267973       6174 [Boot]
 P MS Data                 76267992   76274165       6174 [Boot]
 P MS Data                 76277048   76279927       2880 [EFISECTOR]
 P MS Data                 97055432   97058311       2880 [EFISECTOR]
 P MS Data                 98621616   98624495       2880 [EFISECTOR]
 P Mac HFS                117148623  117250065     101443 [O~T^B]
 P MS Data                118786047  237103102  118317056
```

Partitions where testdisk says they cant be restored after deep search:

```
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63
Check the harddisk size: HD jumpers settings, BIOS detection...
The harddisk (128 GB / 119 GiB) seems too small! (< 1331 GB / 1240 GiB)
The following partitions can't be recovered:
     Mac HFS                  1965219 2600910116 2598944898
     HFS, 1330 GB / 1239 GiB
     Mac HFS                  3066614  765480213  762413600
     HFS, 390 GB / 363 GiB
     Mac HFS                 58002510 1344827318 1286824809 [g]
     HFS, 658 GB / 613 GiB
     Mac HFS                 58002518 1403628735 1345626218 [h]
     HFS, 688 GB / 641 GiB
     Mac HFS                128918299 1242768923 1113850625 [D]
     HFS, 570 GB / 531 GiB
     Mac HFS                129855931 1243706555 1113850625 [D]
     HFS, 570 GB / 531 GiB
     Mac HFS                141829163 1255679787 1113850625 [D]
     HFS, 570 GB / 531 GiB
     Mac HFS                141927467 1255778091 1113850625 [D]
     HFS, 570 GB / 531 GiB
     MS Data                186845208  313245719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186845896  313246407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186846096  313246607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186846208  313246719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186846328  313246839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186846552  313247063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186846936  313247447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847048  313247559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847152  313247663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847240  313247751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847392  313247903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847456  313247967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847592  313248103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847712  313248223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847832  313248343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186847888  313248399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848032  313248543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848120  313248631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848224  313248735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848320  313248831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848424  313248935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848552  313249063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848656  313249167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848760  313249271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186848984  313249495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186849120  313249631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186849544  313250055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186849760  313250271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186849968  313250479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186850232  313250743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186850416  313250927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186850888  313251399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186851064  313251575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186851160  313251671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186851280  313251791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186851472  313251983  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186851664  313252175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186851968  313252479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186852392  313252903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186852568  313253079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186852880  313253391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186853288  313253799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186853680  313254191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186853872  313254383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186853984  313254495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186854040  313254551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186854344  313254855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186854632  313255143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186854800  313255311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186854960  313255471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186855136  313255647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186855248  313255759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186855488  313255999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186855824  313256335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186856080  313256591  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186856240  313256751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186856528  313257039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186856712  313257223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186857040  313257551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186857304  313257815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186857504  313258015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186857672  313258183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186857856  313258367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186858056  313258567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186858312  313258823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186858504  313259015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186858752  313259263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186859000  313259511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186859312  313259823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186859400  313259911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186859576  313260087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186859832  313260343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186860008  313260519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186860416  313260927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186860656  313261167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186860912  313261423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186861232  313261743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186861888  313262399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186862072  313262583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186862168  313262679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186862296  313262807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186862576  313263087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186862664  313263175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186862792  313263303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186863016  313263527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186863224  313263735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186863320  313263831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186864056  313264567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186864272  313264783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186864472  313264983  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186864864  313265375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186864944  313265455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186865048  313265559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186865296  313265807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186865512  313266023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186865664  313266175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186866072  313266583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186866296  313266807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186866608  313267119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186866728  313267239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186866968  313267479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186867392  313267903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186867648  313268159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186867832  313268343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868000  313268511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868160  313268671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868264  313268775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868408  313268919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868520  313269031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868744  313269255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186868944  313269455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186869056  313269567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186869272  313269783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186869312  313269823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186869424  313269935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186869632  313270143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186869960  313270471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186870360  313270871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186870432  313270943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186870680  313271191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186870896  313271407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186871016  313271527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186871352  313271863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186871520  313272031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186871592  313272103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186871872  313272383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872016  313272527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872280  313272791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872456  313272967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872560  313273071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872760  313273271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872888  313273399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186872984  313273495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186873272  313273783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186873440  313273951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186873680  313274191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186873944  313274455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186873992  313274503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186874136  313274647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186874400  313274911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186874472  313274983  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186874672  313275183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186874936  313275447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875088  313275599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875160  313275671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875392  313275903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875552  313276063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875600  313276111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875792  313276303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186875944  313276455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186876320  313276831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186876376  313276887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186876576  313277087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186876816  313277327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186876888  313277399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186877088  313277599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186877480  313277991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186877568  313278079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186877728  313278239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186877792  313278303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878056  313278567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878200  313278711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878456  313278967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878504  313279015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878616  313279127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878680  313279191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186878944  313279455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186879144  313279655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186879256  313279767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186879392  313279903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186879528  313280039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186879720  313280231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186879976  313280487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880064  313280575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880184  313280695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880416  313280927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880552  313281063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880704  313281215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880776  313281287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186880920  313281431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186881112  313281623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186881200  313281711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186881432  313281943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186881632  313282143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186881824  313282335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186881888  313282399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186882120  313282631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186882384  313282895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186882432  313282943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186882632  313283143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186882808  313283319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186883008  313283519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186883544  313284055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186883680  313284191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186883880  313284391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186884056  313284567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186884136  313284647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186884432  313284943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186884512  313285023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186885040  313285551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186885344  313285855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186885536  313286047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186885632  313286143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186885752  313286263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186885904  313286415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186886152  313286663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186886488  313286999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186886840  313287351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186887064  313287575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186887360  313287871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186887504  313288015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186887592  313288103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186887760  313288271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186887992  313288503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186888200  313288711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186888336  313288847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186888384  313288895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186888640  313289151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186888736  313289247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186888864  313289375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889096  313289607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889328  313289839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889408  313289919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889592  313290103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889768  313290279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889872  313290383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186889936  313290447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186890088  313290599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186891640  313292151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186891776  313292287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186891920  313292431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892000  313292511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892112  313292623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892280  313292791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892392  313292903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892440  313292951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892696  313293207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186892880  313293391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186893000  313293511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186893168  313293679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186893264  313293775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186893480  313293991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186893680  313294191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186893832  313294343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186894048  313294559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186894096  313294607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186894216  313294727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186894400  313294911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186894480  313294991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186894664  313295175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186895312  313295823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186895536  313296047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186895840  313296351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186895904  313296415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186896064  313296575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186896568  313297079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186896720  313297231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186896888  313297399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186897072  313297583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186897424  313297935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186897568  313298079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186897648  313298159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186897744  313298255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186897816  313298327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898064  313298575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898192  313298703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898264  313298775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898480  313298991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898816  313299327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898888  313299399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186898968  313299479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186899216  313299727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186899400  313299911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186899616  313300127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186899816  313300327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186900008  313300519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186900240  313300751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186900464  313300975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186900624  313301135  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186900872  313301383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186900920  313301431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186901048  313301559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186901328  313301839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186901464  313301975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186901592  313302103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186901768  313302279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186901960  313302471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902064  313302575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902288  313302799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902360  313302871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902552  313303063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902696  313303207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902816  313303327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186902968  313303479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186903120  313303631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186903328  313303839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186903560  313304071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186903712  313304223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186903760  313304271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186903952  313304463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186904024  313304535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186904160  313304671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186904464  313304975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186904592  313305103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186904768  313305279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186904952  313305463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186905016  313305527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186905432  313305943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186905600  313306111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186905768  313306279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186905968  313306479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186906256  313306767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186906384  313306895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186906896  313307407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186907224  313307735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186907424  313307935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186907648  313308159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186907800  313308311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186908040  313308551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186908448  313308959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186908560  313309071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186908696  313309207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186908848  313309359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186909096  313309607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186909256  313309767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186909408  313309919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186909696  313310207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186909776  313310287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186909936  313310447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186910088  313310599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186910296  313310807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186910400  313310911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186910568  313311079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186910712  313311223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186910920  313311431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186911192  313311703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186911384  313311895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186911536  313312047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186911680  313312191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186911920  313312431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186912064  313312575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186912400  313312911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186912512  313313023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186912672  313313183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186912832  313313343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186912984  313313495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186913128  313313639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186913416  313313927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186913496  313314007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186913760  313314271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186913912  313314423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186914080  313314591  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186914256  313314767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186914400  313314911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186914632  313315143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186914760  313315271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186914920  313315431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186915056  313315567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186915192  313315703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186915328  313315839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186915656  313316167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186915768  313316279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186915920  313316431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186916184  313316695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186916336  313316847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186916488  313316999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186916776  313317287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186916856  313317367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917016  313317527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917160  313317671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917320  313317831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917496  313318007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917640  313318151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917800  313318311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186917984  313318495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186918168  313318679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186918320  313318831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186918464  313318975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186918608  313319119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186918952  313319463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186919064  313319575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186919216  313319727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186919360  313319871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186919528  313320039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186919680  313320191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186919968  313320479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186920048  313320559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186920200  313320711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186920344  313320855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186920504  313321015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186920680  313321191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186920824  313321335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921048  313321559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921288  313321799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921448  313321959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921512  313322023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921696  313322207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921840  313322351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186921960  313322471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186922240  313322751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186922392  313322903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186922536  313323047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186922680  313323191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186922824  313323335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186923152  313323663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186923264  313323775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186923528  313324039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186923712  313324223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186923872  313324383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186924024  313324535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186924176  313324687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186924456  313324967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186924536  313325047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186924784  313325295  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186924936  313325447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186925096  313325607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186925272  313325783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186925416  313325927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186925584  313326095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186925648  313326159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186925784  313326295  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186926128  313326639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186926440  313326951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186926592  313327103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186926736  313327247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186926872  313327383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186927032  313327543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186927360  313327871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186927472  313327983  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186927632  313328143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186927760  313328271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928008  313328519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928168  313328679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928320  313328831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928608  313329119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928688  313329199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928840  313329351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186928984  313329495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186929144  313329655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186929320  313329831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186929464  313329975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186929632  313330143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186929696  313330207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186929824  313330335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186930136  313330647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186930280  313330791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186930416  313330927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186930560  313331071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186930720  313331231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931040  313331551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931152  313331663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931304  313331815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931432  313331943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931584  313332095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931744  313332255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186931896  313332407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186932216  313332727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186932304  313332815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186932464  313332975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186932616  313333127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186932784  313333295  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186932952  313333463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186933088  313333599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186933256  313333767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186933368  313333879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186933560  313334071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186933624  313334135  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186933752  313334263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186934008  313334519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186934272  313334783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186934336  313334847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186934728  313335239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935000  313335511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935056  313335567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935200  313335711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935272  313335783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935392  313335903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935520  313336031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935672  313336183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935880  313336391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186935992  313336503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186936296  313336807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186936416  313336927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186936640  313337151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186936704  313337215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186936840  313337351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186937080  313337591  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186937224  313337735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186937464  313337975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186937664  313338175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186937728  313338239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186937856  313338367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186938096  313338607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186938248  313338759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186938424  313338935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186938576  313339087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186938720  313339231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186938864  313339375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186939032  313339543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186939360  313339871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186939472  313339983  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186939656  313340167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186939848  313340359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186940016  313340527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186940176  313340687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186940328  313340839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186940608  313341119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186940688  313341199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186940848  313341359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186941000  313341511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186941168  313341679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186941336  313341847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186941480  313341991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186941728  313342239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186941880  313342391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186942112  313342623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186942352  313342863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186942592  313343103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186942728  313343239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186942952  313343463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186943112  313343623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186943264  313343775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186943504  313344015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186943664  313344175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186943864  313344375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186944016  313344527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186944160  313344671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186944296  313344807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186944456  313344967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186944600  313345111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186944936  313345447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186945048  313345559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186945280  313345791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186945488  313345999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186945640  313346151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186945824  313346335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186946072  313346583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186946224  313346735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186946496  313347007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186946632  313347143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186946712  313347223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947072  313347583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947184  313347695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947344  313347855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947504  313348015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947656  313348167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947816  313348327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186947984  313348495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186948136  313348647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186948272  313348783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186948424  313348935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186948576  313349087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186948864  313349375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186948944  313349455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186949104  313349615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186949256  313349767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186949416  313349927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186949592  313350103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186949728  313350239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186949976  313350487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186950216  313350727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186950352  313350863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186950576  313351087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186950728  313351239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186950904  313351415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186951088  313351599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186951240  313351751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186951384  313351895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186951528  313352039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186951664  313352175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186951992  313352503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186952104  313352615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186952272  313352783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186952520  313353031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186952680  313353191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186952832  313353343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953112  313353623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953192  313353703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953352  313353863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953496  313354007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953664  313354175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953832  313354343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186953976  313354487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186954184  313354695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186954336  313354847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186954576  313355087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186954744  313355255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186954888  313355399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186955032  313355543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186955176  313355687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186955312  313355823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186955656  313356167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186955768  313356279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186955928  313356439  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186956192  313356703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186956368  313356879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186956536  313357047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186956704  313357215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186956888  313357399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186957176  313357687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186957248  313357759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186957440  313357951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186957592  313358103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186957848  313358359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186957992  313358503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186958280  313358791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186958360  313358871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186958520  313359031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186958672  313359183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186958832  313359343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186959000  313359511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186959144  313359655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186959280  313359791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186959592  313360103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186959744  313360255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186959888  313360399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186960032  313360543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186960176  313360687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186960504  313361015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186960616  313361127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186960736  313361247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186960896  313361407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186961048  313361559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186961208  313361719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186961376  313361887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186961568  313362079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186961864  313362375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186961944  313362455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186962096  313362607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186962248  313362759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186962416  313362927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186962592  313363103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186962736  313363247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186962968  313363479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186963120  313363631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186963264  313363775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186963504  313364015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186963696  313364207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186963848  313364359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186963992  313364503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186964136  313364647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186964272  313364783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186964416  313364927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186964744  313365255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186964856  313365367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186965016  313365527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186965184  313365695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186965448  313365959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186965704  313366215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186965856  313366367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966144  313366655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966224  313366735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966368  313366879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966512  313367023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966680  313367191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966848  313367359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186966984  313367495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186967096  313367607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186967328  313367839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186967592  313368103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186967736  313368247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186967880  313368391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186968016  313368527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186968152  313368663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186968320  313368831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186968680  313369191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186968800  313369311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186968952  313369463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186969128  313369639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186969288  313369799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186969448  313369959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186969592  313370103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186969776  313370287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970064  313370575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970136  313370647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970296  313370807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970456  313370967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970616  313371127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970664  313371175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970824  313371335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186970976  313371487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186971136  313371647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186971424  313371935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186971504  313372015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186971680  313372191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186971832  313372343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186972000  313372511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186972176  313372687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186972320  313372831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186972520  313373031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186972688  313373199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186972928  313373439  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186973072  313373583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186973208  313373719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186973352  313373863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186973696  313374207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186973808  313374319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186973960  313374471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186974112  313374623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186974256  313374767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186974400  313374911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186974568  313375079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186974744  313375255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186975032  313375543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186975104  313375615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186975304  313375815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186975600  313376111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186975760  313376271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186975904  313376415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186976184  313376695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186976264  313376775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186976416  313376927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186976568  313377079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186976728  313377239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186976904  313377415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186977040  313377551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186977152  313377663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186977392  313377903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186977544  313378055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186977608  313378119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186977816  313378327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186978120  313378631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186978264  313378775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186978400  313378911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186978536  313379047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186978680  313379191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979024  313379535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979136  313379647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979280  313379791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979440  313379951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979600  313380111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979752  313380263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186979888  313380399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186980056  313380567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186980216  313380727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186980360  313380871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186980544  313381055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186980832  313381343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186980904  313381415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186981096  313381607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186981352  313381863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186981512  313382023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186981664  313382175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186981952  313382463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186982032  313382543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186982184  313382695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186982336  313382847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186982504  313383015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186982680  313383191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186982824  313383335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983096  313383607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983248  313383759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983392  313383903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983536  313384047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983680  313384191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983824  313384335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186983960  313384471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186984296  313384807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186984408  313384919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186984568  313385079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186984688  313385199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186984848  313385359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186985104  313385615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186985232  313385743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186985344  313385855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186985664  313386175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186985744  313386255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186985896  313386407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186986048  313386559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186986216  313386727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186986392  313386903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186986536  313387047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186986752  313387263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186986920  313387431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186987072  313387583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186987208  313387719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186987352  313387863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186987496  313388007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186987832  313388343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186987944  313388455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186988104  313388615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186988360  313388871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186988568  313389079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186988712  313389223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989000  313389511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989080  313389591  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989232  313389743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989384  313389895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989544  313390055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989720  313390231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186989864  313390375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186990072  313390583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186990336  313390847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186990480  313390991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186990624  313391135  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186990960  313391471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186991072  313391583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186991224  313391735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186991376  313391887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186991632  313392143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186991776  313392287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992056  313392567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992136  313392647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992288  313392799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992440  313392951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992608  313393119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992784  313393295  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186992920  313393431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993040  313393551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993232  313393743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993296  313393807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993544  313394055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993688  313394199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993832  313394343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186993976  313394487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186994112  313394623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186994256  313394767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186994400  313394911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186994728  313395239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186994840  313395351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186994992  313395503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186995216  313395727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186995376  313395887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186995544  313396055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186995696  313396207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186995984  313396495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186996064  313396575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186996224  313396735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186996376  313396887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186996544  313397055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186996720  313397231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186996864  313397375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186997016  313397527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186997224  313397735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186997432  313397943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186997600  313398111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186997744  313398255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186997888  313398399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186998224  313398735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186998336  313398847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186998496  313399007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186998744  313399255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186998904  313399415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186999056  313399567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186999344  313399855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186999424  313399935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186999584  313400095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186999736  313400247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                186999896  313400407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187000064  313400575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187000216  313400727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187000376  313400887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187000512  313401023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187000656  313401167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187000992  313401503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187001104  313401615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187001272  313401783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187001520  313402031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187001680  313402191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187001832  313402343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002112  313402623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002192  313402703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002352  313402863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002504  313403015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002672  313403183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002848  313403359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187002984  313403495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187003104  313403615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187003296  313403807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187003344  313403855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187003616  313404127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187003720  313404231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187003904  313404415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004016  313404527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004136  313404647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004232  313404743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004512  313405023  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004648  313405159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004736  313405247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004896  313405407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187004976  313405487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187005216  313405727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187005384  313405895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187005536  313406047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187005680  313406191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006016  313406527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006128  313406639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006224  313406735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006384  313406895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006536  313407047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006824  313407335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187006904  313407415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007056  313407567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007200  313407711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007368  313407879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007544  313408055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007688  313408199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007808  313408319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187007904  313408415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187008072  313408583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187008232  313408743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187008384  313408895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187008672  313409183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187008752  313409263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187008904  313409415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187009056  313409567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187009224  313409735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187009416  313409927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187009568  313410079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187009936  313410447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010072  313410583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010184  313410695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010400  313410911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010568  313411079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010752  313411263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010824  313411335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187010952  313411463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011080  313411591  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011344  313411855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011408  313411919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011536  313412047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011640  313412151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011736  313412247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011800  313412311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187011904  313412415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012104  313412615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012216  313412727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012272  313412783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012560  313413071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012680  313413191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012760  313413271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187012872  313413383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187013072  313413583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187013256  313413767  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187013416  313413927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187013648  313414159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187013752  313414263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187013944  313414455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014104  313414615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014200  313414711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014400  313414911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014528  313415039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014608  313415119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014720  313415231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014896  313415407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187014944  313415455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187015192  313415703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187015368  313415879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187015480  313415991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187015664  313416175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187015952  313416463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187016032  313416543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187016232  313416743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187016448  313416959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187016808  313417319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187016872  313417383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187017000  313417511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187017144  313417655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187017264  313417775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187017416  313417927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187017640  313418151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187017712  313418223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187018008  313418519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187018136  313418647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187018400  313418911  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187018584  313419095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187018632  313419143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187018824  313419335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187019168  313419679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187019560  313420071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187019704  313420215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187019968  313420479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187020272  313420783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187020464  313420975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187020528  313421039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187020720  313421231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187021024  313421535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187021368  313421879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187021528  313422039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187021816  313422327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187021888  313422399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187022016  313422527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187022144  313422655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187022312  313422823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187022392  313422903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187022744  313423255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187023440  313423951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187023744  313424255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187023904  313424415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187024272  313424783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187024672  313425183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187024728  313425239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187024864  313425375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187024992  313425503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187025096  313425607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187025224  313425735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187025592  313426103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187025960  313426471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187027072  313427583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187029432  313429943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187029792  313430303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187030120  313430631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187030264  313430775  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187030376  313430887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187030440  313430951  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187030632  313431143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187030872  313431383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187031048  313431559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187031368  313431879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187031640  313432151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187031808  313432319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187031880  313432391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187032072  313432583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187032304  313432815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187032584  313433095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187032792  313433303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187032864  313433375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187033056  313433567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187033288  313433799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187033544  313434055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187033712  313434223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187033760  313434271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187033928  313434439  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187034160  313434671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187034384  313434895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187034592  313435103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187034656  313435167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187034832  313435343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187035056  313435567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187035296  313435807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187035456  313435967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187035504  313436015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187035672  313436183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187035904  313436415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187036144  313436655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187036368  313436879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187036432  313436943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187036608  313437119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187036840  313437351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187037080  313437591  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187037272  313437783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187037320  313437831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187037432  313437943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187037664  313438175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187037904  313438415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187038104  313438615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187038240  313438751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187038360  313438871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187038648  313439159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039016  313439527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039240  313439751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039304  313439815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039424  313439935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039656  313440167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039848  313440359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187039952  313440463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187040152  313440663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187040216  313440727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187040336  313440847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187040592  313441103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187040816  313441327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187041048  313441559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187041192  313441703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187041448  313441959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187041632  313442143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187041736  313442247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187041968  313442479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187042120  313442631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187042368  313442879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187042608  313443119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187042856  313443367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187043000  313443511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187043232  313443743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187043416  313443927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187043520  313444031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187043752  313444263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187043904  313444415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187044128  313444639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187044360  313444871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187044584  313445095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187044736  313445247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187044800  313445311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045008  313445519  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045200  313445711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045304  313445815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045536  313446047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045680  313446191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045744  313446255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187045952  313446463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187046184  313446695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187046464  313446975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187046616  313447127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187046680  313447191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187046784  313447295  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187046936  313447447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187047128  313447639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187047232  313447743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187047488  313447999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187047632  313448143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187047704  313448215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187047904  313448415  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187048144  313448655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187048376  313448887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187048536  313449047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187048608  313449119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187048816  313449327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187049000  313449511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187049104  313449615  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187049344  313449855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187049496  313450007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187049560  313450071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187049664  313450175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187050808  313451319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051072  313451583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051328  313451839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051544  313452055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051608  313452119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051680  313452191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051824  313452335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187051936  313452447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187052112  313452623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187052192  313452703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187052336  313452847  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187052448  313452959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187052648  313453159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187052848  313453359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187053024  313453535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187053088  313453599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187053360  313453871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187053616  313454127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187053888  313454399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054048  313454559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054112  313454623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054208  313454719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054328  313454839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054496  313455007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054640  313455151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054696  313455207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054824  313455335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187054936  313455447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187055128  313455639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187055344  313455855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187055464  313455975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187055608  313456119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187055704  313456215  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187055840  313456351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187056112  313456623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187056312  313456823  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187056552  313457063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187056688  313457199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057016  313457527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057152  313457663  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057288  313457799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057536  313458047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057624  313458135  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057736  313458247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057816  313458327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187057960  313458471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187058584  313459095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187058728  313459239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187058832  313459343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187058992  313459503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059128  313459639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059176  313459687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059344  313459855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059432  313459943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059560  313460071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059624  313460135  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059832  313460343  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187059912  313460423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187060120  313460631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187060320  313460831  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187060592  313461103  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187060752  313461263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187060824  313461335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187060992  313461503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061112  313461623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061248  313461759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061352  313461863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061472  313461983  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061648  313462159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061736  313462247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187061960  313462471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187062064  313462575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187062216  313462727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187062280  313462791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187062600  313463111  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187062688  313463199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187062840  313463351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063048  313463559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063144  313463655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063328  313463839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063408  313463919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063584  313464095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063768  313464279  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063920  313464431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187063984  313464495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187064208  313464719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187064464  313464975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187064616  313465127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187064760  313465271  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187064952  313465463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187065120  313465631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187065448  313465959  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187065560  313466071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187065744  313466255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187066056  313466567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187066216  313466727  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187066368  313466879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187066648  313467159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187066728  313467239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187066856  313467367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187067016  313467527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187067168  313467679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187067328  313467839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187067496  313468007  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187067640  313468151  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187067888  313468399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187068064  313468575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187068128  313468639  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187068328  313468839  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187068568  313469079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187068808  313469319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187068992  313469503  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187069144  313469655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187069280  313469791  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187069416  313469927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187069576  313470087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187069912  313470423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070024  313470535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070184  313470695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070344  313470855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070408  313470919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070584  313471095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070744  313471255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187070888  313471399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187071168  313471679  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187071248  313471759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187071408  313471919  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187071552  313472063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187071720  313472231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187071888  313472399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187072024  313472535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187072240  313472751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187072392  313472903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187072544  313473055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187072792  313473303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187072960  313473471  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187073024  313473535  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187073224  313473735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187073480  313473991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187073632  313474143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187073776  313474287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187073912  313474423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187074072  313474583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187074416  313474927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187074528  313475039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187074696  313475207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187074912  313475423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187075064  313475575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187075224  313475735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187075376  313475887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187075664  313476175  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187075744  313476255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187075896  313476407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187076040  313476551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187076208  313476719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187076376  313476887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187076520  313477031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187076800  313477311  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187076952  313477463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187077096  313477607  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187077232  313477743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187077392  313477903  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187077728  313478239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187077840  313478351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187078000  313478511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187078208  313478719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187078456  313478967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187078632  313479143  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187078776  313479287  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079064  313479575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079144  313479655  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079304  313479815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079456  313479967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079616  313480127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079792  313480303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187079936  313480447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187080112  313480623  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187080304  313480815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187080456  313480967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187080608  313481119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187080920  313481431  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187081072  313481583  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187081208  313481719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187081352  313481863  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187081520  313482031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187081864  313482375  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187081976  313482487  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082136  313482647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082184  313482695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082288  313482799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082544  313483055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082608  313483119  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082792  313483303  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187082952  313483463  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187083120  313483631  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187083368  313483879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187083648  313484159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187083728  313484239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187083880  313484391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187084032  313484543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187084200  313484711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187084368  313484879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187084504  313485015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187084728  313485239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187084968  313485479  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187085160  313485671  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187085224  313485735  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187085432  313485943  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187085576  313486087  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187085784  313486295  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187085936  313486447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187086272  313486783  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187086384  313486895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187086520  313487031  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187086672  313487183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187086824  313487335  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187086984  313487495  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187087136  313487647  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187087424  313487935  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187087504  313488015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187087752  313488263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187087896  313488407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187088064  313488575  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187088232  313488743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187088368  313488879  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187088584  313489095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187088752  313489263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187088816  313489327  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187089000  313489511  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187089240  313489751  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187089488  313489999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187089656  313490167  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187089720  313490231  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187089912  313490423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187090056  313490567  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187090248  313490759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187090384  313490895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187090528  313491039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187090696  313491207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187090856  313491367  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187091192  313491703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187091304  313491815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187091568  313492079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187091696  313492207  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187091944  313492455  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187092184  313492695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187092376  313492887  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187092528  313493039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187092808  313493319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187092888  313493399  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093048  313493559  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093200  313493711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093360  313493871  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093544  313494055  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093688  313494199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093848  313494359  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187093912  313494423  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187094040  313494551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187094288  313494799  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187094536  313495047  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187094736  313495247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187094808  313495319  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187094936  313495447  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187095088  313495599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187095248  313495759  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187095488  313495999  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187095688  313496199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187095752  313496263  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187095880  313496391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187096032  313496543  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187096200  313496711  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187096464  313496975  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187096680  313497191  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187096744  313497255  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187096872  313497383  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187097016  313497527  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187097176  313497687  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187097416  313497927  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187097648  313498159  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187097712  313498223  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187097840  313498351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187098088  313498599  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187098344  313498855  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187098552  313499063  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187098616  313499127  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187098736  313499247  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187098880  313499391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187099040  313499551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187099304  313499815  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187099504  313500015  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187099568  313500079  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187099688  313500199  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187099928  313500439  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187100232  313500743  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187100384  313500895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187100528  313501039  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187100672  313501183  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187100840  313501351  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187101184  313501695  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187101296  313501807  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187101456  313501967  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187101584  313502095  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187101880  313502391  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187102040  313502551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187102192  313502703  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187102480  313502991  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187102560  313503071  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187102728  313503239  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187102896  313503407  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187103040  313503551  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187103208  313503719  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
     MS Data                187103384  313503895  126400512
     EXT4 Large file Sparse superblock Recover, 64 GB / 60 GiB
```

Structure after deep search:
```
Disk /dev/sda - 128 GB / 119 GiB - CHS 15566 255 63
     Partition               Start        End    Size in sectors
>D MS Data                     2046    1021947    1019902
 D MS Data                     2048     206847     204800 [NO NAME]
 D MS Data                     2048    1021949    1019902
 D MS Data                     2054     206853     204800 [NO NAME]
 D MS Data                   280582    1304581    1024000
 D MS Data                   280604    1304603    1024000
 D MS Data                   280622    1304621    1024000
 D MS Data                   280666    1304665    1024000
 D MS Data                   280684    1304683    1024000
 D MS Data                   280732    1304731    1024000
 D MS Data                   280750    1304749    1024000
 D MS Data                   280836    1304835    1024000
 D MS Data                   280876    1304875    1024000
 D MS Data                   413694    1433595    1019902
 D MS Data                   413696    1433597    1019902
 D MS Data                   468992  118786047  118317056
 D Mac HFS                   910412    9299021    8388610 [~?~?~?M-:D^A]
 D Mac HFS                  1661111   35215804   33554694
 D Mac HFS                  1806203   35360896   33554694
 D Mac HFS                  1886500   35440937   33554438
 D Mac HFS                  2046654   35601347   33554694
 D MS Data                 13697667   13718405      20739 [NO NAME]
 D MS Data                 16100875   16107048       6174
 D MS Data                 16107048   16113221       6174 [Boot]
 D Mac HFS                 35215801   68770494   33554694
 D Mac HFS                 35260337   35293618      33282
 D Mac HFS                 35293615   35326896      33282
 D Mac HFS                 35322498   35323268        771
 D Mac HFS                 35323265   35324035        771
 D Mac HFS                 35360893   68915586   33554694
 D Mac HFS                 35440934   68995371   33554438
 D Mac HFS                 35601344   69156037   33554694
 D Mac HFS                 58395673  201005850  142610178
 D MS Data                 61602641   62974624    1371984 [GWM-9M-$&#1579;&#1866;M-= b~^dS
 D MS Data                 76249435   76255608       6174
 D MS Data                 76255608   76261781       6174 [Boot]
 D MS Data                 76255627   76261800       6174
 D MS Data                 76261800   76267973       6174 [Boot]
 D MS Data                 76261819   76267992       6174
 D MS Data                 76267992   76274165       6174 [Boot]
 D MS Data                 76277048   76279927       2880 [EFISECTOR]
 D MS Data                 97055432   97058311       2880 [EFISECTOR]
 D MS Data                 98621616   98624495       2880 [EFISECTOR]
 D Mac HFS                117047184  117148626     101443 [O~T^B]
 D Mac HFS                117148623  117250065     101443 [O~T^B]
 D MS Data                118786046  119762941     976896
 D MS Data                118786047  237103102  118317056
 D MS Data                118786048  119762943     976896
 D MS Data                119064580  120041475     976896
 D MS Data                119064610  120041505     976896
 D MS Data                119064628  120041523     976896
 D MS Data                119064638  120041533     976896
 D MS Data                119064704  120041599     976896
 D MS Data                119064724  120041619     976896
 D MS Data                119064784  120041679     976896
 D MS Data                119064824  120041719     976896
 D MS Data                119064870  120041765     976896
 D MS Data                119064918  120041813     976896
 D MS Data                119064968  120041863     976896
 D MS Data                119065016  120041911     976896
 D MS Data                119065066  120041961     976896
 D MS Data                119065182  120042077     976896
 D MS Data                119065228  120042123     976896
 D MS Data                119065242  120042137     976896
 D MS Data                119065324  120042219     976896
 D MS Data                119065352  120042247     976896
 D MS Data                119065448  120042343     976896
 D MS Data                119065514  120042409     976896
 D MS Data                119065574  120042469     976896
 D MS Data                119065618  120042513     976896
 D MS Data                119065666  120042561     976896
 D MS Data                119065712  120042607     976896
 D MS Data                119065768  120042663     976896
 D MS Data                119065826  120042721     976896
 D MS Data                119065880  120042775     976896
 D MS Data                123668478  250068989  126400512
 D MS Data                123668480  250068991  126400512
 D MS Data                155935079  176883775   20948697
 D MS Data                156053567  177002263   20948697
 D MS Data                176883775  197832471   20948697
 D MS Data                177002263  197950959   20948697
 D MS Data                177372047  177392785      20739 [NO NAME]
>D MS Data                177372051  177595734     223684 [NO NAME]
```

---

### Post by YesWeCan on 2014-01-04
This is tricky. I think these three are probably real partitions:
 
[FONT=courier new]```
start sector     end sector     sectors      size             use
       2048         206847       204800     100.00    MiB    EFI
     280582        1304581      1024000     500.00    MiB    linux /boot
   35215801       68770494     33554694      16.00    GiB    linux swap
```
[/FONT]
Still examining to see any signs of / and /home.
Did you have any Windows partitions on sda?

---

### Post by gerwalt on 2014-01-04
Yes, there was one ~50-70gb ntfs partition with windows on it

---

### Post by YesWeCan on 2014-01-04
Would you post the output of
```
swapon -s
```
and then turn swap off
```
sudo swapoff -a
```

I am reading through this: [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

I am trying to figure out how to find the linux root partition. We can mount the /boot partition and see files there, such as Grub files, but I'm not sure it contains info about where the root partition actually is, although grub.cfg will tell us the original partition number and block ID. I haven't used testdisk much myself; I'm surprised it hasn't found the linux root partition.

---

### Post by gerwalt on 2014-01-04
```
Filename                Type        Size    Used    Priority
```

Not very much.

---

### Post by YesWeCan on 2014-01-04
I think these are potentially real partitions, although not all of them as some overlap!

```
GPT      start       end       sectors       size         usage        
1        2048      206847        204800     100.00 MiB     EFI
2      280582     1304581       1024000     500.00 MiB   linux /boot        
4       68992   118786047     118317056      56.42 GiB
      1661111    35215804      33554694      16.00 GiB
5    35215801    68770494      33554694      16.00 GiB   linux swap
6    76255608    98624495      22368888      10.67 GiB
    123668478   250068989     126400512      60.27 GiB
13  118786047   237103102     118317056      56.42 GiB
    186845208   313503895     126658688      60.40 GiB
```
I'd like to scan the starting sectors of some of them to see if an ext4 signature is present. Just need to remember how to do that.

---

### Post by gerwalt on 2014-01-04
I think I read something about dd and hexdump. Would only need to know how the starting sectors look like

---

### Post by YesWeCan on 2014-01-04
Ok, try this. This will show the byte values on the disk for 2048 bytes starting at the given sector. For example, for start sector 76255608:
```
sudo dd if=/dev/sda skip=76255608 bs=512 count=4 | hexdump -C
```

Then look at the row starting 00000430 and across to the 9th column of bytes to see "53 ef" which is the ext4 superblock signature.
See if any of the candidate partitions have this signature.

The output will look like this:
```
00000000  eb 63 90 00 00 00 00 00  00 00 00 00 00 00 00 00  |.c..............|
00000010  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
4+0 records in
4+0 records out
*
00000050  00 00 00 00 00 00 00 00  00 00 00 80 d8 08 4d 0a  |..............M.|
2048 bytes (2.0 kB) copied00000060  00 00 00 00 ff fa 90 90  f6 c2 80 74 05 f6 c2 70  |...........t...p|
00000070  74 02 b2 80 ea 79 7c 00  00 31 c0 8e d8 8e d0 bc  |t....y|..1......|
, 8.3386e-05 s, 24.6 MB/s
00000080  00 20 fb a0 64 7c 3c ff  74 02 88 c2 52 bb 17 04  |. ..d|<.t...R...|
00000090  80 27 03 74 06 be 88 7d  e8 17 01 be 05 7c b4 41  |.'.t...}.....|.A|
000000a0  bb aa 55 cd 13 5a 52 72  3d 81 fb 55 aa 75 37 83  |..U..ZRr=..U.u7.|
000000b0  e1 01 74 32 31 c0 89 44  04 40 88 44 ff 89 44 02  |..t21..D.@.D..D.|
000000c0  c7 04 10 00 66 8b 1e 5c  7c 66 89 5c 08 66 8b 1e  |....f..\|f.\.f..|
000000d0  60 7c 66 89 5c 0c c7 44  06 00 70 b4 42 cd 13 72  |`|f.\..D..p.B..r|
000000e0  05 bb 00 70 eb 76 b4 08  cd 13 73 0d f6 c2 80 0f  |...p.v....s.....|
000000f0  84 d0 00 be 93 7d e9 82  00 66 0f b6 c6 88 64 ff  |.....}...f....d.|
00000100  40 66 89 44 04 0f b6 d1  c1 e2 02 88 e8 88 f4 40  |@f.D...........@|
00000110  89 44 08 0f b6 c2 c0 e8  02 66 89 04 66 a1 60 7c  |.D.......f..f.`||
00000120  66 09 c0 75 4e 66 a1 5c  7c 66 31 d2 66 f7 34 88  |f..uNf.\|f1.f.4.|
00000130  d1 31 d2 66 f7 74 04 3b  44 08 7d 37 fe c1 88 c5  |.1.f.t.;D.}7....|
00000140  30 c0 c1 e8 02 08 c1 88  d0 5a 88 c6 bb 00 70 8e  |0........Z....p.|
00000150  c3 31 db b8 01 02 cd 13  72 1e 8c c3 60 1e b9 00  |.1......r...`...|
00000160  01 8e db 31 f6 bf 00 80  8e c6 fc f3 a5 1f 61 ff  |...1..........a.|
00000170  26 5a 7c be 8e 7d eb 03  be 9d 7d e8 34 00 be a2  |&Z|..}....}.4...|
00000180  7d e8 2e 00 cd 18 eb fe  47 52 55 42 20 00 47 65  |}.......GRUB .Ge|
00000190  6f 6d 00 48 61 72 64 20  44 69 73 6b 00 52 65 61  |om.Hard Disk.Rea|
000001a0  64 00 20 45 72 72 6f 72  0d 0a 00 bb 01 00 b4 0e  |d. Error........|
000001b0  cd 10 ac 3c 00 75 f4 c3  00 00 00 00 00 00 00 00  |...<.u..........|
000001c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000400  00 00 28 00 00 ff 9f 00  f3 ff 07 00 eb d3 74 00  |..(...........t.|
00000410  59 04 1a 00 00 00 00 00  02 00 00 00 02 00 00 00  |Y...............|
00000420  00 80 00 00 00 80 00 00  00 20 00 00 81 ef c7 52  |......... .....R|
00000430  cd fa 72 50 cb 01 ff ff  [COLOR=#ff0000]53 ef[/COLOR] 01 00 01 00 00 00  |..rP....S.......|
00000440  a2 f3 72 50 00 00 00 00  00 00 00 00 01 00 00 00  |..rP............|
00000450  00 00 00 00 0b 00 00 00  00 01 00 00 3c 00 00 00  |............<...|
00000460  46 02 00 00 7b 00 00 00  26 15 0e 59 f5 75 42 ef  |F...{...&..Y.uB.|
00000470  ae 64 3b 90 5a ca 96 a0  55 62 75 6e 74 75 00 00  |.d;.Z...Ubuntu..|
00000480  00 00 00 00 00 00 00 00  2f 00 6e 74 00 00 00 00  |......../.nt....|
00000490  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
000004c0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 fd 03  |................|
000004d0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000004e0  08 00 00 00 00 00 00 00  5f 82 1c 00 a0 c2 d6 e9  |........_.......|
000004f0  e6 cf 4e c3 b9 76 f0 4a  f1 25 46 df 01 01 00 00  |..N..v.J.%F.....|
00000500  0c 00 00 00 00 00 00 00  a2 f3 72 50 0a f3 02 00  |..........rP....|
00000510  04 00 00 00 00 00 00 00  00 00 00 00 ff 7f 00 00  |................|
00000520  00 80 48 00 ff 7f 00 00  01 00 00 00 ff ff 48 00  |..H...........H.|
00000530  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000540  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 08  |................|
00000550  00 00 00 00 00 00 00 00  00 00 00 00 1c 00 1c 00  |................|
00000560  01 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000570  00 00 00 00 04 00 00 00  06 41 82 10 00 00 00 00  |.........A......|
00000580  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
*
00000800

```

---

### Post by gerwalt on 2014-01-04
```
GPT      start       end       sectors       size         usage        
1        2048      206847        204800     100.00 MiB     EFI
2      280582     1304581       1024000     500.00 MiB   linux /boot        
4       68992   118786047     118317056      56.42 GiB
      1661111    35215804      33554694      16.00 GiB
5    35215801    68770494      33554694      16.00 GiB   linux swap
6    76255608    98624495      22368888      10.67 GiB
    123668478   250068989     126400512      60.27 GiB
13  118786047   237103102     118317056      56.42 GiB
    186845208   313503895     126658688      60.40 GiB
```

combined it with grep to find it faster

```
Start                                        contains "53 ef"
2048                                        no
280582                                 yes at 00000430 9th column
68992                                    no
1661111                            no
35215801                        no
76255608                        no
123668478                     no
118786047                    yes at 00000630 9th column
186845208                   yes at 00000430 9th column
```

---

### Post by YesWeCan on 2014-01-04
Good. It is *likely* that either 118786048 or 186845208 are starts of usable linux ext4 partitions. Not sure why the former was 1 sector out in the GPT partition table. Anyhow, we can proceed to rebuild the MBR and then try to mount the candidate partitions.

First, output the existing MBR partition table and store it in a text file called "mbrtable" or whatever you like to call it:
```
sudo sfdisk -d /dev/sda > mbrtable
```
You can open this in gedit to change the sector numbers.
I'll post what the edited table should look like in a few moments...

---

### Post by gerwalt on 2014-01-04
Just to remember you, I'm using a GPT. I know there are things mixed up, but I know, that I created a GPT table before I installed Windows and Ubuntu 18 month ago.

```
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > partitiontable

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.
```

---

### Post by YesWeCan on 2014-01-04
Oh yes. Delete the GPT header first.
```
sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda
```

---

### Post by gerwalt on 2014-01-04
So we replace the GPT with a MBR? Does that work and is it important for the existing data to either have GPT or MBR?

---

### Post by YesWeCan on 2014-01-04
Then edit "mbrtable" to look like this:
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=   280582, size=  1024000, Id=83
/dev/sda2 : start=118786048, size=118317056, Id=83
/dev/sda3 : start=186845208, size=126658688, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0
```

This only chnages the table in the MBR, not the rest of the disk. This will make the disk appear to have 3 partitions: the linux boot and the two candidates for / or /home. This will not boot yet but we may be able to see what's there and then decide what to do next.

Once you have edited mbrtable, write it back to the disk's MBR:
```
sudo sh -c "cat mbrtable | sfdisk /dev/sda"
```

---

### Post by gerwalt on 2014-01-04
Thank you for the clarification. The data is of course most important to me. I dont really have a problem with setting up the system from scratch.


I still cant read the table after deleting the GPT. But I'm not sure if I still have to read it, if I overwrite it with your information.

```
ubuntu@ubuntu:~$ sudo dd if=/dev/zero bs=512 count=1 seek=1 of=/dev/sda
1+0 records in
1+0 records out
512 bytes (512 B) copied, 0.00112427 s, 455 kB/s
ubuntu@ubuntu:~$ sudo sfdisk -d /dev/sda > mbrtable

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util sfdisk doesn't support GPT. Use GNU Parted.
```

---

### Post by YesWeCan on 2014-01-04
Deleting the GPT header means there is no chance of using the GPT partition table to recover your data. I am assuming this doesn't work anyhow. Instead, we can create an equivalent MBR partition table for the partitions that we believe are correct.

The existing data doesn't care what sort of partition table exists except for the booting systems. These will be broken. However, they are already broken.

As I indicated earlier, I think the disk is in a mangled state. So getting anything back off it will be lucky.

However, if you wish to take the disk to, say, a professional recovery person then you should not write anything to it.

---

### Post by YesWeCan on 2014-01-04
It may be that sfdisk now looks for the backup GPT table at the end of the disk. It has been a while since I've done this.
While I look this up, try writing the new MBR table to the disk.

---

### Post by YesWeCan on 2014-01-04
Try
```
sudo hdparm -z /dev/sda
```
before using sfdisk. This causes the kernel to re-read the disk partition table.

---

### Post by gerwalt on 2014-01-04
I'm sorry. I'm totally fine with what you suggest, I was just a little irritated with the whole GPT/MBR stuff and wanted to be sure.

-------------------------------------------------------

I used the mbrtable that you gave me and sfdisk is giving me the following error:

```
ubuntu@ubuntu:~$ sudo sh -c "cat mbrtable | sfdisk /dev/sda"
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     17-     18-    140290+  ee  GPT
/dev/sda2       2192+   4280-   2089-  16777347   af  HFS / HFS+
/dev/sda3         17+     81-     64-    512000   83  Linux
/dev/sda4       1002+   1003-      1-      3087    7  HPFS/NTFS/exFAT
Warning: given size (126658688) exceeds max allowable size (0)

sfdisk: bad input
```

---

### Post by gerwalt on 2014-01-04
> **YesWeCan said:**
> Try
```
sudo hdparm -z /dev/sda
```
before using sfdisk. This causes the kernel to re-read the disk partition table.

Will try that now, forget the post before this one

---

### Post by gerwalt on 2014-01-04
Ok hdparm worked well. sfdisk is giving the same error as two posts before

---

### Post by YesWeCan on 2014-01-04
Ok, the size of the last partition is too big for the size of the disk. I copied the size from the dodgy GPT table! The last sector on the disk is 268435455 so I reckon the size of sda3 should be no more than 81590248 (39GiB).
Try this table:
```
# partition table of /dev/sda
unit: sectors
/dev/sda1 : start=   280582, size=  1024000, Id=83
/dev/sda2 : start=118786048, size=118317056, Id=83
/dev/sda3 : start=186845208, size= 81590248, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0

```

---

### Post by gerwalt on 2014-01-04
Same result as before (just the last line is different)

```
ubuntu@ubuntu:~$ sudo sh -c "cat mbrtable | sfdisk /dev/sda"
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     17-     18-    140290+  ee  GPT
/dev/sda2       2192+   4280-   2089-  16777347   af  HFS / HFS+
/dev/sda3         17+     81-     64-    512000   83  Linux
/dev/sda4       1002+   1003-      1-      3087    7  HPFS/NTFS/exFAT
Warning: given size (81590248) exceeds max allowable size (0)

sfdisk: bad input
```

---

### Post by YesWeCan on 2014-01-04
Oh, the total number of sectors is 250069680. I mistook 128GB for 128GiB.
Try a sda3 sector size of 63224473

---

### Post by YesWeCan on 2014-01-04
Or maybe 63224472. Or just something smaller until it works.

---

### Post by gerwalt on 2014-01-04
Yes, everything I wrote is in GB, not GiB.

Error stays the same:

```
ubuntu@ubuntu:~$ sudo sh -c "cat mbrtable | sfdisk /dev/sda"
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     17-     18-    140290+  ee  GPT
/dev/sda2       2192+   4280-   2089-  16777347   af  HFS / HFS+
/dev/sda3         17+     81-     64-    512000   83  Linux
/dev/sda4       1002+   1003-      1-      3087    7  HPFS/NTFS/exFAT
Warning: given size (63224473) exceeds max allowable size (0)

sfdisk: bad input
```

---

### Post by gerwalt on 2014-01-04
> **YesWeCan said:**
> Or maybe 63224472. Or just something smaller until it works.

I think the biggest that will work is 0, given the warning of sfdisk

---

### Post by gerwalt on 2014-01-04
> **YesWeCan said:**
> Or maybe 63224472. Or just something smaller until it works.

Ok, this actually worked, but 2 partitions overlap now:

```
ubuntu@ubuntu:~$ sudo sh -c "cat mbrtable | sfdisk /dev/sda"
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     17-     18-    140290+  ee  GPT
/dev/sda2       2192+   4280-   2089-  16777347   af  HFS / HFS+
/dev/sda3         17+     81-     64-    512000   83  Linux
/dev/sda4       1002+   1003-      1-      3087    7  HPFS/NTFS/exFAT
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1        280582   1304581    1024000  83  Linux
/dev/sda2     118786048 237103103  118317056  83  Linux
/dev/sda3     186845208 250069679   63224472  83  Linux
/dev/sda4             0         -          0   0  Empty
Warning: partitions 2 and 2 overlap

sfdisk: I don't like these partitions - nothing changed.
(If you really want this, use the --force option.)
```

---

### Post by YesWeCan on 2014-01-04
Same mistake again - I copied the GPT partition size for sda2. The size of sda2 needs to be reduced as well.
The size of sda2 should be 68059160 to stop the overlap.

---

### Post by YesWeCan on 2014-01-04
```
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=   280582, size=  1024000, Id=83
/dev/sda2 : start=118786048, size= 68059160, Id=83
/dev/sda3 : start=186845208, size= 63224472, Id=83
/dev/sda4 : start=        0, size=        0, Id= 0

```

---

### Post by gerwalt on 2014-01-04
Now it works, except the warnings that the partitions are not bound to cylinders.

```
ubuntu@ubuntu:~$ sudo sh -c "cat mbrtable | sfdisk /dev/sda"
Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 15566 cylinders, 255 heads, 63 sectors/track
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+     17-     18-    140290+  ee  GPT
/dev/sda2       2192+   4280-   2089-  16777347   af  HFS / HFS+
/dev/sda3         17+     81-     64-    512000   83  Linux
/dev/sda4       1002+   1003-      1-      3087    7  HPFS/NTFS/exFAT
New situation:
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1        280582   1304581    1024000  83  Linux
/dev/sda2     118786048 186845207   68059160  83  Linux
/dev/sda3     186845208 250069679   63224472  83  Linux
/dev/sda4             0         -          0   0  Empty
Warning: partition 1 does not start at a cylinder boundary
Warning: partition 1 does not end at a cylinder boundary
Warning: partition 2 does not start at a cylinder boundary
Warning: partition 2 does not end at a cylinder boundary
Warning: partition 3 does not start at a cylinder boundary
Warning: partition 3 does not end at a cylinder boundary
Warning: no primary partition is marked bootable (active)
This does not matter for LILO, but the DOS MBR will not boot this disk.
Successfully wrote the new partition table

Re-reading the partition table ...

If you created or changed a DOS partition, /dev/foo7, say, then use dd(1)
to zero the first 512 bytes:  dd if=/dev/zero of=/dev/foo7 bs=512 count=1
(See fdisk(8).)
```

---

### Post by YesWeCan on 2014-01-04
Now run
```
sudo fdisk -l /dev/sda
```
to confirm the MBR partition table is as we want.

Next, try to mount sda1 and see what it contains. It ought to look like /boot.
```
sudo mount /dev/sda1 /mnt
```

---

### Post by gerwalt on 2014-01-04
fdisk still claims the drive to have a GPT, Partitions look good

```
ubuntu@ubuntu:~$ sudo fdisk -l /dev/sda

WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 128.0 GB, 128035676160 bytes
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1          280582     1304581      512000   83  Linux
/dev/sda2       118786048   186845207    34029580   83  Linux
/dev/sda3       186845208   250069679    31612236   83  Linux
```

Parted doesnt complain:

```
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA SAMSUNG SSD 830 (scsi)
Disk /dev/sda: 250069680s
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start       End         Size       Type     File system  Flags
 1      280582s     1304581s    1024000s   primary  ext4
 2      118786048s  186845207s  68059160s  primary  ext4
 3      186845208s  250069679s  63224472s  primary
```

Mounting does not work:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

Output of dmesg is:

```
[18980.898605] EXT4-fs (sda1): ext4_check_descriptors: Block bitmap for group 0 not in group (block 4294967294)!
[18980.898611] EXT4-fs (sda1): group descriptors corrupted!
```

---

### Post by YesWeCan on 2014-01-04
Doesn't look good. That partition looked like the most likely to be intact. Try the other two.

---

### Post by gerwalt on 2014-01-04
Well sda2 seems to work, sda3 doesnt:

```
ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt


ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt
mount: wrong fs type, bad option, bad superblock on /dev/sda3,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

dmesg for those two look more promising:

```
[18926.257673] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[18942.384760] EXT4-fs (sda3): bad geometry: block count 15800064 exceeds size of device (7903059 blocks)
```

How can I access the data on sda2? "mount -l" says its mounted on /mnt, but I cant find it anywhere.

---

### Post by YesWeCan on 2014-01-04
```
ls /mnt
```

The error is because the size of the partition is too large for the size of the filesystem.

---

### Post by gerwalt on 2014-01-04
I think a different mount point would be better? This seems like something from the live OS

```
ubuntu@ubuntu:~$ ll /mnt/
total 118441
drwxr-xr-x 5 root root     4096 Dec  5 21:10 ./
drwxr-xr-x 1 root root      260 Jan  4 14:19 ../
-rw-r--r-- 1 root root   919745 Sep 10 22:29 abi-3.8.0-31-generic
-rw-r--r-- 1 root root   919810 Oct 23 11:42 abi-3.8.0-33-generic
-rw-r--r-- 1 root root   919810 Nov 12 19:28 abi-3.8.0-34-generic
-rw-r--r-- 1 root root   154960 Sep 10 22:29 config-3.8.0-31-generic
-rw-r--r-- 1 root root   154961 Oct 23 11:42 config-3.8.0-33-generic
-rw-r--r-- 1 root root   154961 Nov 12 19:28 config-3.8.0-34-generic
drwxr-xr-x 2 root root     1024 Nov  1  2012 efi/
drwxr-xr-x 5 root root     1024 Jan  2 19:25 grub/
-rw-r--r-- 1 root root 30796589 Sep 28 11:17 initrd.img-3.8.0-31-generic
-rw-r--r-- 1 root root 30799018 Nov 11 17:50 initrd.img-3.8.0-33-generic
-rw-r--r-- 1 root root 30800042 Dec  3 09:18 initrd.img-3.8.0-34-generic
drwx------ 2 root root    12288 Nov  1  2012 lost+found/
-rw-r--r-- 1 root root   176764 Dec  5  2012 memtest86+.bin
-rw-r--r-- 1 root root   178944 Dec  5  2012 memtest86+_multiboot.bin
-rw------- 1 root root  3062541 Sep 10 22:29 System.map-3.8.0-31-generic
-rw------- 1 root root  3062707 Oct 23 11:42 System.map-3.8.0-33-generic
-rw------- 1 root root  3062653 Nov 12 19:28 System.map-3.8.0-34-generic
-rw------- 1 root root  5362320 Sep 10 22:29 vmlinuz-3.8.0-31-generic
-rw------- 1 root root  5364816 Oct 23 11:42 vmlinuz-3.8.0-33-generic
-rw------- 1 root root  5364080 Nov 12 19:28 vmlinuz-3.8.0-34-generic
```

---

### Post by gerwalt on 2014-01-04
Ok, created a differnent folder for the mount point and it seems to be the correct content. But the efi/ folder is empty.

---

### Post by YesWeCan on 2014-01-04
This is a /boot partition. It may or may not be the correct one. It's worth taking a look at grub/grub.cfg.
Unfortunately, we still haven't found / or /home, tho.

---

### Post by gerwalt on 2014-01-04
I remember the "Windows" entry at the end of the grub.cfg. Seems to be mine.

```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
set root='hd0,gpt6'
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt6 --hint-efi=hd0,gpt6 --hint-baremetal=ahci0,gpt6  5bb9b055-184d-4fd5-acf7-90c295e94ca2
else
  search --no-floppy --fs-uuid --set=root 5bb9b055-184d-4fd5-acf7-90c295e94ca2
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
    set gfxpayload="${1}"
    if [ "${1}" = "keep" ]; then
        set vt_handoff=vt.handoff=7
    else
        set vt_handoff=
    fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
recordfail
    load_video
    gfxmode $linux_gfx_mode
    insmod gzio
    insmod part_gpt
    insmod ext2
    set root='hd0,gpt4'
    if [ x$feature_platform_search_hint = xy ]; then
      search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
    else
      search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
    fi
    linux    /vmlinuz-3.8.0-34-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro   quiet splash $vt_handoff
    initrd    /initrd.img-3.8.0-34-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    menuentry 'Ubuntu, with Linux 3.8.0-34-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-advanced-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
        else
          search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
        fi
        echo    'Loading Linux 3.8.0-34-generic ...'
        linux    /vmlinuz-3.8.0-34-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-34-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-34-generic-recovery-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
        else
          search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
        fi
        echo    'Loading Linux 3.8.0-34-generic ...'
        linux    /vmlinuz-3.8.0-34-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-34-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-33-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-33-generic-advanced-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
        else
          search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
        fi
        echo    'Loading Linux 3.8.0-33-generic ...'
        linux    /vmlinuz-3.8.0-33-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-33-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-33-generic-recovery-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
        else
          search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
        fi
        echo    'Loading Linux 3.8.0-33-generic ...'
        linux    /vmlinuz-3.8.0-33-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-33-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-31-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-31-generic-advanced-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    recordfail
        load_video
        gfxmode $linux_gfx_mode
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
        else
          search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
        fi
        echo    'Loading Linux 3.8.0-31-generic ...'
        linux    /vmlinuz-3.8.0-31-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro   quiet splash $vt_handoff
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-31-generic
    }
    menuentry 'Ubuntu, with Linux 3.8.0-31-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.8.0-31-generic-recovery-5bb9b055-184d-4fd5-acf7-90c295e94ca2' {
    recordfail
        load_video
        insmod gzio
        insmod part_gpt
        insmod ext2
        set root='hd0,gpt4'
        if [ x$feature_platform_search_hint = xy ]; then
          search --no-floppy --fs-uuid --set=root --hint-bios=hd0,gpt4 --hint-efi=hd0,gpt4 --hint-baremetal=ahci0,gpt4  849ea212-8008-42f4-b440-f67f8a8687be
        else
          search --no-floppy --fs-uuid --set=root 849ea212-8008-42f4-b440-f67f8a8687be
        fi
        echo    'Loading Linux 3.8.0-31-generic ...'
        linux    /vmlinuz-3.8.0-31-generic root=UUID=5bb9b055-184d-4fd5-acf7-90c295e94ca2 ro recovery nomodeset 
        echo    'Loading initial ramdisk ...'
        initrd    /initrd.img-3.8.0-31-generic
    }
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.

menuentry "Windows" {
    search --fs-uuid --no-floppy --set=root 887D-F3E4
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

---

### Post by YesWeCan on 2014-01-04
> [18942.384760] EXT4-fs (sda3): bad geometry: block count 15800064 exceeds size of device (7903059 blocks)
This means that the size of the partition is too small for the size of the ext4 filesystem. The ext4 filesystem
uses 4096 byte blocks whereas the disk uses 512 byte logical sectors. So 7903059 blocks = 63224472 sectors, the
size of sda3.

The filesystem seems to be 15800064 blocks or 126400512 sectors or 60GiB. This is impossible because the disk is
not big enough. I am pondering how this might have come to be.

The filesystem may be repaired using fsck and then mounted to see what data remains. You need to look up how to
use fsck.

---

### Post by gerwalt on 2014-01-05
Could it be, that sda2 is too big? Currently it is about 30GB big and that is way too much for a /boot partition. Is there any information in the ext4 superblock about the size of a partition? Like in most protocol headers?

Does the total block count help to find out the size of the partition and thus the beginning of the next partition?
[https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout#The_Super_Block](https://ext4.wiki.kernel.org/index.php/Ext4_Disk_Layout#The_Super_Block)


Will set up Linux on a spare drive, to not be dependent on the Live OS. If you tell me something to do and it is better to do that from a Live OS, please tell me so ;)

---

### Post by gerwalt on 2014-01-05
```
ubuntu@ubuntu:~$ sudo fsck -n /dev/sda1
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
Error reading block 4294967295 (Invalid argument).  Ignore error? no

Superblock has an invalid journal (inode 8).
Clear? no

fsck.ext4: Illegal inode number while checking ext3 journal for /dev/sda1

/dev/sda1: ********** WARNING: Filesystem still has errors **********

ubuntu@ubuntu:~$ echo $?
12
```

12 means Filesystem errors left uncorrected and Operational error

```

[LIST]
[*]4 – Filesystem errors left uncorrected
[*]8 – Operational error
[/LIST]

```

sda2 looks fine, although its too big (my opinion)

```
ubuntu@ubuntu:~$ sudo fsck -n /dev/sda2
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
/dev/sda2: clean, 254/122400 files, 151105/488448 blocks
ubuntu@ubuntu:~$ echo $?
0
```

sda3 looks like sda1:

```
ubuntu@ubuntu:~$ sudo fsck -n /dev/sda3
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
fsck.ext4: Group descriptors look bad... trying backup blocks...
fsck.ext4: Bad magic number in super-block when using the backup blocks
fsck.ext4: going back to original superblock
Error reading block 1367597501 (Invalid argument).  Ignore error? no

Superblock has an invalid journal (inode 8).
Clear? no

fsck.ext4: Illegal inode number while checking ext3 journal for /dev/sda3

/dev/sda3: ********** WARNING: Filesystem still has errors **********

ubuntu@ubuntu:~$ echo $?
12
```

---

### Post by gerwalt on 2014-01-06
Can I trust fsck to repair the paritions or should I prefer to change the mbrtable manually?

---

### Post by oldfred on 2014-01-06
did you have this and get them out of sync?
Do not mix gpt & MBR is the bottom line.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by gerwalt on 2014-01-06
Cant really say if I had a mixed GPT/MBR.

At least gdisk said that the MBR is hybrid and GPT damaged. That was before we started rewriting the partition table to MBR.

My intention when installing the system with Windows and Linux was to have both using GPT. But I cant say for sure, that I havent done any mistakes when installing it 1 1/2 year ago.

---

### Post by oldfred on 2014-01-06
Windows only boots from gpt drives with UEFI. And must have UEFI to boot from a gpt partitioned drive.
Ubuntu will boot with BIOS or UEFI from gpt drive.
Both Windows and Ubuntu only boot from MBR(msdos) drives with BIOS.

---

### Post by gerwalt on 2014-01-07
> **oldfred said:**
> Windows only boots from gpt drives with UEFI. And must have UEFI to boot from a gpt partitioned drive.
Ubuntu will boot with BIOS or UEFI from gpt drive.
Both Windows and Ubuntu only boot from MBR(msdos) drives with BIOS.

Yes, I know that (now). The problem is I messed up the GPT partition table with testdisk and YesWeCan and I tried to remove the GPT and replace it with a MBR. But we could only restore the boot partition.


I tried the "Partition Wizard" which was suggested in the sevenforums. It shows all my files for the NTFS partition on the SSD. Will try to recover the needed files from that partition with "Power Recovery Tool" by the same company. Here are two screenshots from that tool.

The first is just the overview of the tool, the second is the result of the full scan for lost partitions and the third as well. The selected NTFS partition is the one I can open and read files from. I'm still wondering, why the /boot partition is in the middle of the drive. I'm pretty sure I have put it at the beginning.

[ATTACH=CONFIG]249294[/ATTACH][ATTACH=CONFIG]249295[/ATTACH][ATTACH=CONFIG]249296[/ATTACH]

Dont know if this helps to solve the problem with the linux partitions

---

### Post by oldfred on 2014-01-07
It may just be easier to recover what data you can and start all over with a good partition plan.

And create a good regular backup plan. With multiple drives you can do quick backups daily with cron & rsync. But I also do copies to  DVDs of most critical files.

---

### Post by gerwalt on 2014-01-07
I will do that later with the Windows partition (probably not today anymore). Just need some bootable tool for that.

The problem is my home partition that was encrypted by Ubuntu. And I'm not sure if I had a lot of data that I hadnt backed up. The things that I remember were some settings and configurations for some programs and tools, but that is not important to me. Dont know if I had any personal files like images or other documents on it, though I have most of that stuff on an external drive and backed up.

YesWeCan already gave me some tips for a partition plan. But any additional information is much appreciated.


Will read this article, when I have recovered everything and set up my system again: [http://www.jveweb.net/en/archives/2011/02/using-rsync-and-cron-to-automate-incremental-backups.html](http://www.jveweb.net/en/archives/2011/02/using-rsync-and-cron-to-automate-incremental-backups.html)

---

### Post by oldfred on 2014-01-07
If you have encryption, then backup is even more important as data recovery is not supposed to be possible or the entire reason for the encryption in the first place.

I do not use encryption, but understand some need it. But not sure all data needs to be encrypted.
I am a believer in Pareto principle or the 80/20 rule and believe that applies to our computer data. It may even be more like 90/10 as I find I have little really vital data.
So I do try to separate system from data. And I include the user settings in /home as part of system. So I keep data in separate data partition(s).

---

### Post by gerwalt on 2014-01-08
Yes, I'm thinking about leaving out the encryption with the new system. But I will wait with that, until I have tried everything to recover the old system.

---

### Post by gerwalt on 2014-01-11
After I found the exact sector beginning and end of the NTFS partition with MiniTool Power Wizard, I kept looking for ext4 superblocks after that partition with the following command:

```
$ [COLOR=#C20CB9][FONT=Consolas]**sudo**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#C20CB9][FONT=Consolas]**dd**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#007800][FONT=Consolas]if[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**/**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]dev[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**/**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]sdb [/FONT][/COLOR][COLOR=#007800][FONT=Consolas]of[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**/**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]dev[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**/**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]stdout [/FONT][/COLOR][COLOR=#007800][FONT=Consolas]bs[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]512[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#007800][FONT=Consolas]skip[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]1304581[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#007800][FONT=Consolas]count[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]1000[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**|**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#C20CB9][FONT=Consolas]**hexdump**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#660033][FONT=Consolas]-C[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#000000][FONT=Consolas]**|**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#C20CB9][FONT=Consolas]**grep**[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#660033][FONT=Consolas]-e[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] [/FONT][/COLOR][COLOR=#FF0000][FONT=Consolas]'......30  .. .. .. .. .. .. .. ..  53 ef .. .. .. .. .. ..'[/FONT][/COLOR]

```

*if* has to be the drive where you want to search, *skip* is the current offset from where you start looking. hexdump outputs the bytes. With grep I looked for rows that ended on i30, where i has to be even. "53 ef" is the ext4 superblock.

After that I could use mount to try to mount that point:

```
$ sudo mount -o offset=$(([COLOR=#000000][FONT=Consolas]1304581[/FONT][/COLOR] * 512)) /dev/sda /mnt/whereever
```

I used the offset and bytesize and mount it whereever I want.


Finally I found the / partition and thus the /home partition. As my /home partition was encrypted I used 

```
$ sudo ecryptfs-recover-private
```

to recover my data. The only thing you need for that is the wrapped-passphrase and your passphrase you used to encrypt the home folder.

ecryptfs-recover-private will mount the drive as read-only in /tmp/.


As I only want to recover my data and now install a fresh system I will mark this as solved.

Thanks again to YesWeCan for his help!

---

