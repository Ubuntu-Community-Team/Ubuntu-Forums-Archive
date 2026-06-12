---
title: "MBR to GPT = lost USB disk capacity."
date: 2017-06-10
forum: General Help
---

### Post by smithbox on 2017-06-10
Hello, everybody.
```
lsb_release -aLSB Version:    core-9.20160110ubuntu5-amd64:core-9.20160110ubuntu5-noarch:security-9.20160110ubuntu5-amd64:security-9.20160110ubuntu5-noarch
Distributor ID:    Ubuntu
Description:    Ubuntu 16.10
Release:    16.10
Codename:    yakkety

```
My name is Mark and I have an issue with my externat USB, 4 TiB drive.
Until now on /dev/sdb was only one partition /dev/sdb1 size 2.1 TiB, rest about 1.9 TiB unsigned. File system NTFS.
Because MBR partitioning table is limited to working only with disks < 2 TiB, i decided to convert MBR to GPT partition table.
Used this page as support: [URL="https://cookuop.co.uk/extendntfs/"]https://cookuop.co.uk/extendntfs/
Used command:
```
[/URL]ntfsresize -s 4000786997248 -f -n  /dev/sdb1
```[ https://manpages.debian.org/testing/ntfs-3g/ntfsresize.8.en.html]("https://cookuop.co.uk/extendntfs/")
_After I wrote and restart my computer, I was totally suprised._
There is no expected 1.9 free space to use, instead disk seems to be fully filled?!
```
parted -l
Model: Seagate Expansion Desk (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name                  Flags
 1      32.3kB  3994GB  3994GB  ntfs         Basic data partition  msftdata
```
```
df -BM
/dev/sdb1       3809315M 3809314M        1M 100% /media/mike/Seagate

```
```
ncdu /media/mike/SEAGATE
       1.0 TiB [#########] /-1WIN                                                                                                                                             
  402.0 GiB [###       ] /- 2LIN
  344.4 GiB [###       ] /DOK
  166.3 GiB [#         ] /ARCHIWUM
   28.6 GiB [          ] /ZGODY
   24.3 GiB [          ] /- 4UNIX
    4.8 GiB [          ] /--- PRZENIESIONE__KOPIE..
    4.2 GiB [          ] /LIC
    1.1 GiB [          ] /PAT
  354.3 MiB [          ] /- MS - DOS
  104.7 MiB [          ] /.Trash-1000
   35.7 MiB [          ] /- 3MAC
    8.1 MiB [          ] /- 32 - 64 bit

                                                                                                                                      
                                                                                                                                      
Total disk usage:   2.0 TiB  Apparent size:   2.0 TiB  Items: 1474396
```
```
fdisk -l
Disk /dev/sdb: 3.7 TiB, 4000787029504 bytes, 7814037167 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 0EBC06E1-5858-9090-8081-828310111213


Device     Start        End    Sectors  Size Type
/dev/sdb1     63 7801475915 7801475853  3.6T Microsoft basic data


Partition 1 does not start on physical sector boundary.
```
Disk Usage Analyzer - [http://imgur.com/a/90ULV](http://imgur.com/a/90ULV)
System Monitor - [http://imgur.com/a/Ty56Q](http://imgur.com/a/Ty56Q)
GParted LiveCD can not find USB drive and freeze.

I spend many hours looking for solution in Internet, and honestly I do not understand it.
How could I recover 1.9 TiB free space on sda USB disk?
Please help.

Regards.
Mark:(

---

### Post by Autodave on 2017-06-10
I am no expert here at all. so hopefully someone else will jump in. But, it appears to me that you have not done anything with the 1.9 part of the drive. Did you format that partition? Did you even create a partition with the remaining 1.9t? Go into settings and find the programs "disks". BE CAREFUL!! Make sure that you are choosing the correct disk! That will show you if there is a partition for the remaining 1.9t. And, it will give you the option to create a partition for the remaining 1.9, or you can remove the current partition and create a new one for the entire drive. Many options there. Again, just make sure that you are choosing the right drive so that you don't wipe the wrong one!

---

### Post by smithbox on 2017-06-10
Misunderstanding.
My aim was, and I done "existing partition sdb1 on disk sdb - extension" from existing 2.1 TiB to 4 TiB (entire capacity)
I was NOT going to create additional partition sdb2 on this disk.

---

### Post by Autodave on 2017-06-10
OK: now I am confused. What is the drive formatted to now and what do you actually want it to be formatted to?

---

### Post by Autodave on 2017-06-10
Is this drive a logical extension of another drive?

---

### Post by smithbox on 2017-06-10
At the moment, this is Basic data partition.
```
parted -l
Model: Seagate Expansion Desk (scsi)
Disk /dev/sdb: 4001GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      32.3kB  3994GB  3994GB  ntfs         Basic data partition  msftdata



```
[URL="http://imgur.com/a/6klI9"]http://imgur.com/a/6klI9
```
gdisk /dev/sdb
GPT fdisk (gdisk) version 1.0.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

```
[/URL]
I can not format it, contain important data.

---

### Post by oldfred on 2017-06-10
It looks like you converted to gpt and expanded the one NTFS partition to entire drive. 
Did you run chkdsk on the NTFS partition.
Windows requires chkdsk on NTFS partitions after a resize and you can only do that from Windows.
The NTFS partition requires the same start & size info in the partition boot sector as the partition table. Chkdsk fixes that.

On a large drive like that as one large partition, chkdsk or defrag may take a long time.

---

### Post by smithbox on 2017-06-10
What about data on disk, I am afraid to lose it when I do:
```
**chkdsk sdb: /f**
```
[http://www.minitool.com/data-recovery/recover-data-after-chkdsk.html](http://www.minitool.com/data-recovery/recover-data-after-chkdsk.html)

---

### Post by oldfred on 2017-06-10
That is why you always have important data well backed up.
But Windows requires chkdsk after resize and if abnormal shutdown amoung several reasons. 
Ubuntu used to automatically run fsck after every 40 or 60 reboots, but with ext4 does not automatically do it.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
[http://askubuntu.com/questions/2596/comparison-of-backup-tools](http://askubuntu.com/questions/2596/comparison-of-backup-tools)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by smithbox on 2017-06-10
> That is why you always have important data well backed up.
100% agree with this statement.
> But Windows requires chkdsk after resize
I had no chance, I resized partition and data simultaneously, unfortunately (:-(
[https://cookuop.co.uk/extendntfs/](https://cookuop.co.uk/extendntfs/)
I,am afraid, that first I will have to temporary get a new disk min 3 TiB and copy all important data.
The risk factor is to high.

More info:
```
 ntfsresize -i /dev/sdb1
ntfsresize v2016.2.22AR.1 (libntfs-3g)
Device name        : /dev/sdb1
NTFS volume version: 3.1
Cluster size       : 512 bytes
Current volume size: 3994355636736 bytes (3994356 MB)
Current device size: 3994355636736 bytes (3994356 MB)
Checking filesystem consistency ...
100.00 percent completed
Accounting clusters ...
Cluster accounting failed at 6450053101 (0x18073ffed): extra cluster in $Bitmap
Cluster accounting failed at 6450053102 (0x18073ffee): extra cluster in $Bitmap
Cluster accounting failed at 6450053103 (0x18073ffef): extra cluster in $Bitmap
Cluster accounting failed at 6450053104 (0x18073fff0): extra cluster in $Bitmap
Cluster accounting failed at 6450053105 (0x18073fff1): extra cluster in $Bitmap
Cluster accounting failed at 6450053106 (0x18073fff2): extra cluster in $Bitmap
Cluster accounting failed at 6450053107 (0x18073fff3): extra cluster in $Bitmap
Cluster accounting failed at 6450053108 (0x18073fff4): extra cluster in $Bitmap
Cluster accounting failed at 6450053109 (0x18073fff5): extra cluster in $Bitmap
Cluster accounting failed at 6450053110 (0x18073fff6): extra cluster in $Bitmap
Cluster accounting failed at 6450053111 (0x18073fff7): extra cluster in $Bitmap
Cluster accounting failed at 6450053112 (0x18073fff8): extra cluster in $Bitmap
Cluster accounting failed at 6450053113 (0x18073fff9): extra cluster in $Bitmap
Cluster accounting failed at 6450053114 (0x18073fffa): extra cluster in $Bitmap
Cluster accounting failed at 6450053115 (0x18073fffb): extra cluster in $Bitmap
Cluster accounting failed at 6450053116 (0x18073fffc): extra cluster in $Bitmap
Cluster accounting failed at 6450053117 (0x18073fffd): extra cluster in $Bitmap
Cluster accounting failed at 6450053118 (0x18073fffe): extra cluster in $Bitmap
Cluster accounting failed at 6450053119 (0x18073ffff): extra cluster in $Bitmap
ntfs_attr_pread_i: ntfs_pread failed: Input/output error
ERROR(5): Couldn't get $Bitmap $DATA: Input/output error
```

```
Chkdsk G:
The main file table is corrupt. Windows will attempt to recover the main file table from disk. Windows can not recover the main file table
```

In this situation, I have to make data copies in the first place! No data backup.
Backup would result in transfer of corrupt file structure and re-loss of 1.9 TiB, which in fact should be at my disposal.
Unless someone tells me how to back up the data itself, and not the whole partition with the free space?

---

