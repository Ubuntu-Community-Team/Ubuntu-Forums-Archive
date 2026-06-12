---
title: "How to correct GPT table and GPT PMBR"
date: 2015-05-07
forum: General Help
---

### Post by f(fanta) on 2015-05-07
When running **fdisk -l**, I get the following errors:

[B]The backup GPT table is corrupt, but the primary appears OK, so that will be used.
GPT PMBR size mismatch (457179135 != 250069679) will be corrected by w(rite).
GPT PMBR size mismatch (457179135 != 457179647) will be corrected by w(rite).[/B]

How do I correct those errors? It took me so much effort to make Ubuntu boot on my laptop, that before risking to do some damage, I would like to get some advice.

Here below the full output of **fdisk -l** . Note that the laptop has only one mass storage, which is a pair of SSDs with RAID 0 (128 GB each). Ubuntu is server 15.04 64-bit, in a dual-boot configuration with WIndows 7 Pro 64-bit.

Thanks!

```
fanta@ono-sendai7:~$ sudo fdisk -l
[COLOR=#ff0000]The backup GPT table is corrupt, but the primary appears OK, so that will be used.[/COLOR]

Disk /dev/sdb: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 31A9B441-4C85-4860-A639-379B8DCEBB02

Device         Start       End   Sectors  Size Type
/dev/sdb1       2048    206847    204800  100M EFI System
/dev/sdb2     206848    468991    262144  128M Microsoft reserved
/dev/sdb3     468992 216512511 216043520  103G Microsoft basic data
/dev/sdb4  216514560 250068991  33554432   16G Linux filesystem

[COLOR=#ff0000]GPT PMBR size mismatch (457179135 != 250069679) will be corrected by w(rite).[/COLOR]

Disk /dev/sda: 119.2 GiB, 128035676160 bytes, 250069680 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x08e50c4e

Device     Boot Start       End   Sectors  Size Id Type
/dev/sda1           1 457179135 457179135  218G ee GPT
[COLOR=#ff0000]
GPT PMBR size mismatch (457179135 != 457179647) will be corrected by w(rite).[/COLOR]

Disk /dev/mapper/isw_bdchijbibj_ASUS_OS: 218 GiB, 234075979776 bytes, 457179648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 131072 bytes
Disklabel type: gpt
Disk identifier: AF78E232-3826-427D-93EA-5FB7738B6165

Device                                  Start       End   Sectors   Size Type
/dev/mapper/isw_bdchijbibj_ASUS_OS1      2048    206847    204800   100M EFI System
/dev/mapper/isw_bdchijbibj_ASUS_OS2    206848   2050047   1843200   900M Windows recovery environment
/dev/mapper/isw_bdchijbibj_ASUS_OS3   2050048   2312191    262144   128M Microsoft reserved
/dev/mapper/isw_bdchijbibj_ASUS_OS4   2312192 335542271 333230080 158.9G Microsoft basic data
/dev/mapper/isw_bdchijbibj_ASUS_OS5 335542272 355074047  19531776   9.3G Linux swap
/dev/mapper/isw_bdchijbibj_ASUS_OS6 355074048 457177087 102103040  48.7G Linux filesystem

Disk /dev/mapper/isw_bdchijbibj_ASUS_RAID0: 20.5 GiB, 21986803712 bytes, 42942976 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 131072 bytes / 131072 bytes

```

---

### Post by oldfred on 2015-05-07
Fdisk used to not work at all on gpt partitioned drives, it just reported that drive was gpt partitioned.
Better to use parted, gparted or gdisk. Gdisk has been the command line tool for gpt drives.

Post these:
 sudo parted -l
or
sudo parted /dev/sda unit s print
or
sudo gdisk -l /dev/sda

      
 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by f(fanta) on 2015-05-08
I see. Thanks. Here the output of the commands:

```
fanta@ono-sendai7:~$ [COLOR=#b22222]**sudo parted -l**[/COLOR]
[sudo] password for fanta: 
Error: Invalid argument during seek for read on /dev/sda
Retry/Ignore/Cancel? Cancel
Model: ATA SanDisk SD5SF212 (scsi)
Disk /dev/sda: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? Cancel                                                         
Model: ATA SanDisk SD5SF212 (scsi)
Disk /dev/sdb: 128GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Error: /dev/mapper/isw_bdchijbibj_ASUS_RAID0: unrecognised disk label
Model: Linux device-mapper (striped) (dm)                                 
Disk /dev/mapper/isw_bdchijbibj_ASUS_RAID0: 22.0GB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS6: 52.3GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system  Flags
 1      0.00B  52.3GB  52.3GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS5: 10.0GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  10.0GB  10.0GB  linux-swap(v1)


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS4: 171GB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  171GB  171GB  ntfs


Error: /dev/mapper/isw_bdchijbibj_ASUS_OS3: unrecognised disk label
Model: Linux device-mapper (linear) (dm)                                  
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS3: 134MB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS2: 944MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  944MB  944MB  ntfs


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS1: 105MB
Sector size (logical/physical): 512B/512B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system  Flags
 1      0.00B  105MB  105MB  fat32


Warning: Not all of the space available to /dev/mapper/isw_bdchijbibj_ASUS_OS appears to be used, you
can fix the GPT to use all of the space (an extra 512 blocks) or continue with the current setting? 
Fix/Ignore? Ignore                                                        
Model: Linux device-mapper (striped) (dm)
Disk /dev/mapper/isw_bdchijbibj_ASUS_OS: 234GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  106MB   105MB   fat32           EFI system partition          boot, esp
 2      106MB   1050MB  944MB   ntfs            Basic data partition          hidden, diag
 3      1050MB  1184MB  134MB                   Microsoft reserved partition  msftres
 4      1184MB  172GB   171GB   ntfs            Basic data partition          msftdata
 5      172GB   182GB   10.0GB  linux-swap(v1)
 6      182GB   234GB   52.3GB  ext4


fanta@ono-sendai7:~$[COLOR=#b22222]** sudo parted /dev/sda unit s print**[/COLOR]
Error: Invalid argument during seek for read on /dev/sda
Retry/Ignore/Cancel? Cancel                                               
Model: ATA SanDisk SD5SF212 (scsi)
Disk /dev/sda: 250069680s
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 
fanta@ono-sendai7:~$ [COLOR=#b22222]**sudo gdisk -l /dev/sda**[/COLOR]
GPT fdisk (gdisk) version 0.8.10

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
Disk /dev/sda: 250069680 sectors, 119.2 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): AF78E232-3826-427D-93EA-5FB7738B6165
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 457179102
Partitions will be aligned on 2048-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848         2050047   900.0 MiB   2700  Basic data partition
   3         2050048         2312191   128.0 MiB   0C01  Microsoft reserved ...
   4         2312192       335542271   158.9 GiB   0700  Basic data partition
   5       335542272       355074047   9.3 GiB     8200  
   6       355074048       457177087   48.7 GiB    8300  
fanta@ono-sendai7:~$ 

```

---

### Post by f(fanta) on 2015-05-08
Also, here is the output of the "v" command of gdisk /dev/sda

```
Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 250069680 sectors, needs to be 457179136 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: GPT claims the disk is larger than it is! (Claimed last usable
sector is 457179102, but backup header is at
457179135 and disk size is 250069680 sectors.
The 'e' option on the experts' menu will probably fix this problem

Problem: partition 4 is too big for the disk.

Problem: partition 5 is too big for the disk.

Problem: partition 6 is too big for the disk.

Partition(s) in the protective MBR are too big for the disk! Creating a
fresh protective or hybrid MBR is recommended.

Identified 8 problems!

```

---

### Post by oldfred on 2015-05-08
I do not know if RAID makes a difference. 
Best to back up partition table with sgdisk and copy file table to another device.
 sudo sgdisk --backup=table /dev/sda

The MBR partition table with gpt, is just for protection from old tools like fdisk. It is to show that drive is partitioned. Usually the MBR has just one full drive entry and it has a MBR type of gpt. 
Using gdisk repairs will normally rewrite MBR table, unless you have hybrid MBR/gpt which in most cases you do not want. 
But on Mac where Windows has to be in BIOS mode on a gpt drive you use hybrid configuration. Windows sees MBR and the Mac & Linux see gpt. And they must be in sync.

 [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

I would then just run the fixes with gdisk.

---

### Post by JohnAreBee on 2015-06-19
> **f(fanta) said:**
> When running **fdisk -l**, I get the following errors:

[B]The backup GPT table is corrupt, but the primary appears OK, so that will be used.
GPT PMBR size mismatch (457179135 != 250069679) will be corrected by w(rite).
GPT PMBR size mismatch (457179135 != 457179647) will be corrected by w(rite).[/B]

How do I correct those errors? It took me so much effort to make Ubuntu boot on my laptop, that before risking to do some damage, I would like to get some advice.

Here below the full output of **fdisk -l** . Note that the laptop has only one mass storage, which is a pair of SSDs with RAID 0 (128 GB each). Ubuntu is server 15.04 64-bit, in a dual-boot configuration with WIndows 7 Pro 64-bit.

Thanks!



[LIST]
[*]Are you using RAID? 
[*]If so what type of RAID? 
[*]Have you recently edited your array? Online migration or expansion of any type? 
[/LIST]
      
The reason I ask is because I have noticed a similar error on one of my arrays after performing an online array expansion and I am interested in any info you have come across researching your issue. I will do the same with anything I come across. In my case at least it is obvious what happened, I added drives to my array and that somehow created this issue. There is nothing wrong with the array as far as I can tell so I have not stressed the issue, and I have not tried to do anything to the array in order to fix the error in fear of screwing it up, at least until I get some more information on the issue. You can see what is causing my error, and maybe yours, by looking at the f/gdisk outputs below.

Here is my fdisk -l output (This info is correct and is AFTER my online RAID migration):
```
GPT PMBR size mismatch (3906732031 != 1565130751) will be corrected by w(rite).

Disk /dev/sdd: 2.7 TiB, 3000370200576 bytes, 5860098048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 29A1C527-80A7-4FCB-95E3-02FA43EAE2C8

Device     Start        End    Sectors  Size Type
/dev/sdd1   4096 3906731998 3906727903  1.8T Linux filesystem
```

Here is my gdisk -i output (This info was correct during initial creation/instalation of Ubuntu):
```
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 15FA33EB-D6C0-4E4A-A848-C215A543CFC1
First sector: 4096 (at 2.0 MiB)
Last sector: 3906731998 (at 1.8 TiB)
Partition size: 3906727903 sectors (1.8 TiB)
Attribute flags: 0000000000000000
Partition name: 'Linux filesystem'
```

---

### Post by oldfred on 2015-06-19
If you use gpt and run the experts mode you should be able to fix the mis-match between MBR & gpt.

       More repair info:
[http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802](http://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table/386802#386802)
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk](http://askubuntu.com/questions/460233/cant-restore-my-gpt-data-with-gdisk)

---

