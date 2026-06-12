---
title: "ext3 reads as NTFS - why?"
date: 2005-08-26
forum: General Help
---

### Post by Irony on 2005-08-26
I used gparted to format hda4 from NTFS to ext3 format (see [http://www.ironclub.net/ubuntu/gparted.png](http://www.ironclub.net/ubuntu/gparted.png) ). I then created a folder and mounted the newly formatted ext3 partition and changed permissions to it so I could read, write, execute - this all worked; 

[PHP]irony@ubuntu:~$ sudo mkdir /media/UBb
irony@ubuntu:~$ sudo mount /dev/hda4 /media/UBb/
irony@ubuntu:~$ sudo chmod 777 /media/UBb/
irony@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       14618    57673350    5  Extended
/dev/hda3           14619       19840    41945715    7  HPFS/NTFS
/dev/hda4           19841       24792    39776940    7  HPFS/NTFS
/dev/hda5   *        7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris[/PHP]

However the fdisk -l command still shows hda4 as NTFS, why is this?

---

### Post by Juergen on 2005-08-26
AFAIK you can 'mark' a partition one type with fdisk but then format it with another fs.
I don't know what consequences a mismatch has, though.

If you don't have data on it, try 'sudo fdisk /dev/hda', then 'm' to see the options.
't' is 'change type' (german system for me, but I don't think they changed the commands)

I'd surely change it, but again, I don't know what disadvantages you get if type and real fs don't match (other than being confused...)
But since its a new partition I think you should change it.

---

### Post by arnieboy on 2005-08-26
> **Irony]I used gparted to format hda4 from NTFS to ext3 format (see [http://www.ironclub.net/ubuntu/gparted.png](http://www.ironclub.net/ubuntu/gparted.png) ). I then created a folder and mounted the newly formatted ext3 partition and changed permissions to it so I could read, write, execute - this all worked said:**
> irony@ubuntu:~$ sudo mkdir /media/UBb
irony@ubuntu:~$ sudo mount /dev/hda4 /media/UBb/
irony@ubuntu:~$ sudo chmod 777 /media/UBb/
irony@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       14618    57673350    5  Extended
/dev/hda3           14619       19840    41945715    7  HPFS/NTFS
/dev/hda4           19841       24792    39776940    7  HPFS/NTFS
/dev/hda5   *        7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris[/PHP]

However the fdisk -l command still shows hda4 as NTFS, why is this?


try doing a:
sudo umount /media/UBb
followed by:
sudo mount -t ext3 /dev/hda4 /media/UBb

---

### Post by Irony on 2005-08-27
Thanks all, I did what Juergen suggested and on booting up today all seems well. Here's what I did;

[PHP]irony@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       14618    57673350    5  Extended
/dev/hda3           14619       19840    41945715    7  HPFS/NTFS
/dev/hda4           19841       24792    39776940    7  HPFS/NTFS
/dev/hda5   *        7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris

Disk /dev/hdb: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1401    11253501    c  W95 FAT32 (LBA)
irony@ubuntu:~$ sudo fdisk /dev/hda

The number of cylinders for this disk is set to 24792.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): m
Command action
   a   toggle a bootable flag
   b   edit bsd disklabel
   c   toggle the dos compatibility flag
   d   delete a partition
   l   list known partition types
   m   print this menu
   n   add a new partition
   o   create a new empty DOS partition table
   p   print the partition table
   q   quit without saving changes
   s   create a new empty Sun disklabel
   t   change a partition's system id
   u   change display/entry units
   v   verify the partition table
   w   write table to disk and exit
   x   extra functionality (experts only)

Command (m for help): l

 0  Empty           1e  Hidden W95 FAT1 80  Old Minix       be  Solaris boot
 1  FAT12           24  NEC DOS         81  Minix / old Lin bf  Solaris
 2  XENIX root      39  Plan 9          82  Linux swap / So c1  DRDOS/sec (FAT-
 3  XENIX usr       3c  PartitionMagic  83  Linux           c4  DRDOS/sec (FAT-
 4  FAT16 <32M      40  Venix 80286     84  OS/2 hidden C:  c6  DRDOS/sec (FAT-
 5  Extended        41  PPC PReP Boot   85  Linux extended  c7  Syrinx
 6  FAT16           42  SFS             86  NTFS volume set da  Non-FS data
 7  HPFS/NTFS       4d  QNX4.x          87  NTFS volume set db  CP/M / CTOS / .
 8  AIX             4e  QNX4.x 2nd part 88  Linux plaintext de  Dell Utility
 9  AIX bootable    4f  QNX4.x 3rd part 8e  Linux LVM       df  BootIt
 a  OS/2 Boot Manag 50  OnTrack DM      93  Amoeba          e1  DOS access
 b  W95 FAT32       51  OnTrack DM6 Aux 94  Amoeba BBT      e3  DOS R/O
 c  W95 FAT32 (LBA) 52  CP/M            9f  BSD/OS          e4  SpeedStor
 e  W95 FAT16 (LBA) 53  OnTrack DM6 Aux a0  IBM Thinkpad hi eb  BeOS fs
 f  W95 Ext'd (LBA) 54  OnTrackDM6      a5  FreeBSD         ee  EFI GPT
10  OPUS            55  EZ-Drive        a6  OpenBSD         ef  EFI (FAT-12/16/
11  Hidden FAT12    56  Golden Bow      a7  NeXTSTEP        f0  Linux/PA-RISC b
12  Compaq diagnost 5c  Priam Edisk     a8  Darwin UFS      f1  SpeedStor
14  Hidden FAT16 <3 61  SpeedStor       a9  NetBSD          f4  SpeedStor
16  Hidden FAT16    63  GNU HURD or Sys ab  Darwin boot     f2  DOS secondary
17  Hidden HPFS/NTF 64  Novell Netware  b7  BSDI fs         fd  Linux raid auto
18  AST SmartSleep  65  Novell Netware  b8  BSDI swap       fe  LANstep
1b  Hidden W95 FAT3 70  DiskSecure Mult bb  Boot Wizard hid ff  BBT
1c  Hidden W95 FAT3 75  PC/IX

Command (m for help): t
Partition number (1-6): 4
Hex code (type L to list codes): 83
Changed system type of partition 4 to 83 (Linux)

Command (m for help): p

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       14618    57673350    5  Extended
/dev/hda3           14619       19840    41945715    7  HPFS/NTFS
/dev/hda4           19841       24792    39776940   83  Linux
/dev/hda5   *        7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris

Command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.

WARNING: Re-reading the partition table failed with error 16: Device or resource  busy.
The kernel still uses the old table.
The new table will be used at the next reboot.
Syncing disks.
irony@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       14618    57673350    5  Extended
/dev/hda3           14619       19840    41945715    7  HPFS/NTFS
/dev/hda4           19841       24792    39776940   83  Linux
/dev/hda5   *        7439       14323    55303731   83  Linux
/dev/hda6           14324       14618     2369556   82  Linux swap / Solaris

Disk /dev/hdb: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1401    11253501    c  W95 FAT32 (LBA)
irony@ubuntu:~$[/PHP]

I've only just seen what arnieboy suggests, so I'll keep that in my ubuntu folder.

---

