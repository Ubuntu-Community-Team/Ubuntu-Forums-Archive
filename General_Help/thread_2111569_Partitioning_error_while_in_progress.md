---
title: "Partitioning error while in progress"
date: 2013-02-02
forum: General Help
---

### Post by SmileFQ on 2013-02-02
As my system drive was getting to small i decided to make it bigger using partition manager. Unfortunately it didn't worked out so well.It did cause a error shown below in the report.

```
Move partition ‘/dev/sda4’ to the right by 82.90 GiB and shrink it from 554.72 GiB to 471.82 GiB 
Job: Check file system on partition ‘/dev/sda4’ 
Command: ntfsresize -P -i -f -v /dev/sda4 
ntfsresize v2011.4.12AR.4 (libntfs-3g)
Device name        : /dev/sda4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 595625423360 bytes (595626 MB)
Current device size: 595625425920 bytes (595626 MB)
Checking for bad sectors ...
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 372673 MB (62.6%)
Collecting resizing constraints ...
Estimating smallest shrunken size supported ...
File feature         Last used at      By inode
$MFT               :    321675 MB             0
Multi-Record       :    595626 MB        190408
$MFTMirr           :    297813 MB             1
Sparse             :    534927 MB        287167
Ordinary           :    595614 MB        228867
You might resize at 372672184320 bytes or 372673 MB (freeing 222953 MB).
Please make a test run using both the -n and -s options before real resizing! 
Check file system on partition ‘/dev/sda4’: Success
Job: Resize file system on partition ‘/dev/sda4’ to 989,475,480 sectors 
Resizing file system from 1,163,330,910 to 989,475,480 sectors. 
Command: ntfsresize -P -f /dev/sda4 -s 506611445760 
ntfsresize v2011.4.12AR.4 (libntfs-3g)
Device name        : /dev/sda4
NTFS volume version: 3.1
Cluster size       : 4096 bytes
Current volume size: 595625423360 bytes (595626 MB)
Current device size: 595625425920 bytes (595626 MB)
New volume size    : 506611442176 bytes (506612 MB)
Checking filesystem consistency ...
Accounting clusters ...
Space in use       : 372673 MB (62.6%)
Collecting resizing constraints ...
Needed relocations : 4297703 (17604 MB)
Schedule chkdsk for NTFS consistency check at Windows boot time ...
Resetting $LogFile ... (this might take a while)
Relocating needed data ...
Updating $BadClust file ...
Updating $Bitmap file ...
Updating Boot record ...
Syncing device ...
Successfully resized NTFS on device '/dev/sda4'.
You can go on to shrink the device for example with Linux fdisk.
IMPORTANT: When recreating the partition, make sure that you
  1)  create it at the same disk sector (use sector as the unit!)
  2)  create it with the same partition type (usually 7, HPFS/NTFS)
  3)  do not make it smaller than the new NTFS filesystem size
  4)  set the bootable flag for the partition if it existed before
Otherwise you won't be able to access NTFS or can't boot from the disk!
If you make a mistake and don't have a partition table backup then you
can recover the partition table by TestDisk or Parted's rescue mode. 
Resize file system on partition ‘/dev/sda4’ to 989,475,480 sectors: Success
Job: Set geometry of partition ‘/dev/sda4’: Start sector: 86,927,715, length: 989,475,480 
Set geometry of partition ‘/dev/sda4’: Start sector: 86,927,715, length: 989,475,480: Success
Job: Set geometry of partition ‘/dev/sda4’: Start sector: 260,783,145, length: 989,475,480 
Could not set geometry for partition ‘/dev/sda4’ while trying to resize/move it. 
Set geometry of partition ‘/dev/sda4’: Start sector: 260,783,145, length: 989,475,480: Error
Moving partition ‘/dev/sda4’ failed. 
Resizing/moving partition ‘/dev/sda4’ failed. 
Move partition ‘/dev/sda4’ to the right by 82.90 GiB and shrink it from 554.72 GiB to 471.82 GiB: Error
```

I managed to enter the partition again using Testdisk. But cant see any partition in the partition manager so i still cant resolve the problem of the small OS drive. What should i do now? Searching the web did not help me futher....

Fdisk output:

```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00063778

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      976895      487424   83  Linux
/dev/sda2          976896    79101951    39062528   83  Linux
/dev/sda3        79101952    86915055     3906552   82  Linux swap / Solaris
/dev/sda4        86915115  1250274689   581679787+   f  W95 Ext'd (LBA)
/dev/sda5        86927715  1076403187   494737736+   7  HPFS/NTFS/exFAT

Disk /dev/sdb: 15.5 GB, 15513354240 bytes
49 heads, 49 sectors/track, 12619 cylinders, total 30299520 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        8064    30299519    15145728    c  W95 FAT32 (LBA)

```

---

### Post by Mark Phelps on 2013-02-02
Unless I misread your post, it looks like you were trying to resize an NTFS partition using Linux filesystem utilities.

My own experience has been that Windows utilities work best with Windows filesystems; Linux utilities with Linux filesystems.

If you can get to a working Windows PC, you should Google for and download the Minitool Partition Wizard Boot CD -- and burn that to CD.

That is a Windows-based partitioning tool and it has the option to recover partitions.  It's worth a shot to see if this can fix the partition problem.

---

### Post by SmileFQ on 2013-02-02
I guess that testdisk fixed the partitions now... but i still cant see them in for example gpartition....

```
Disk /dev/sda - 640 GB / 596 GiB - CHS 77826 255 63                                               
     Partition               Start        End    Size in sectors                                  
>* Linux                    0  32 33    60 206 18     974848                                      
 P Linux                   60 206 19  4923 221 34   78125056                                      
 P Linux Swap            4923 221 35  5410  54  4    7813104                                      
 L HPFS - NTFS           5411   0  1 67002 254 56  989475473 [Data] 
```

---

