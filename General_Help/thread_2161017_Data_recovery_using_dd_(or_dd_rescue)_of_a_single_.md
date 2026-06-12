---
title: "Data recovery using dd (or dd_rescue) of a single partition"
date: 2013-07-09
forum: General Help
---

### Post by c.monty on 2013-07-09
Hello!

I have a 3TB harddisk that is filled with data, but the harddisk is identified with only 2TB.
```
knoppix@Microknoppix:~$ sudo fdisk -l
Disk /dev/sda: 2000.4 GB, 2000421444608 bytes
255 heads, 63 sectors/track, 243204 cylinders, total 3907073134 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes

```

Can I recover the data starting with the first sector after GPT header data?
The disk is partitioned using gdisk, and therefore the partition starts at LBA address 2048.

What would be the correct syntax to read out data of the partition?

THX

---

### Post by sudodus on 2013-07-09
Before doing anything more, try to view the content with some other tools:

```
 gksudo gparted
```

```
 sudo gdisk -l /dev/sdX
```

```
 sudo parted -l
```

Can any of those tools see more than 2 TB and/or some partitions?

What operating system version etc are you running? Check with

```
uname -a
```

Do you have data exceeding those 2 TB? In that case, the system, that should run ddrescue (which I think is better than dd and dd_rescue) must also see more than 2 TB, unless [maybe if] you can succeed with direct access. Read carefully

```
info ddrescue
```

which is well written and explains how to use the tool.

---

### Post by oldfred on 2013-07-09
fdisk does not work on gpt drives and only will show the protective MBR's partition table which has the 2TB limit. As sudodus suggests see what gdisk and parted show as they recognize gpt partitioned drives. If you configured with some sort of hybrid configuration be very careful. fdisk should only have one entry for the entire gpt partition table, but cannot show more than the 2TB because there is not space. Designed 30 years ago when 1GB was huge and 2TB was beyond anything conceived for a PC.
       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by c.monty on 2013-07-10
Here's the output of the different commands:
```

knoppix@Microknoppix:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.5

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
Disk /dev/sda: 3907073134 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): EC0AFC0B-A206-4FCF-B68A-3B3D06D16221
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 5860533134
Partitions will be aligned on 2048-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048      5860533134   2.7 TiB     8300  Linux filesystem

knoppix@Microknoppix:~$ sudo parted -l
Error: Das Argument ist ungültig during seek for read on /dev/sda         
Retry/Ignore/Cancel? i                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will be used.
OK/Cancel? ok                                                             
Backtrace has 8 calls on stack:
  8: /lib/i386-linux-gnu/libparted.so.0(ped_assert+0x29) [0xb76c92a9]
  7: /lib/i386-linux-gnu/libparted.so.0(+0x4b6de) [0xb77076de]
  6: /lib/i386-linux-gnu/libparted.so.0(ped_disk_new+0x61) [0xb76d1171]
  5: parted() [0x804e71b]
  4: parted() [0x804f780]
  3: parted(main+0x1953) [0x804ddd3]
  2: /lib/i386-linux-gnu/libc.so.6(__libc_start_main+0xe6) [0xb752ae16]
  1: parted() [0x804de25]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

	http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

	http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

	parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at ../../../libparted/labels/gpt.c:718 in
function _parse_header() failed.

knoppix@Microknoppix:~$ sudo uname -a
Linux Microknoppix 3.6.11 #12 SMP PREEMPT Thu Dec 20 04:04:10 CET 2012 i686 GNU/Linux

```

---

### Post by sudodus on 2013-07-10
I think it is important to be very careful, when trying to repair this disk, so I suggest that you wait for advice from *oldfred* before doing anything more.

---

### Post by oldfred on 2013-07-10
Use gdisks commands to update backup gpt partition table.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

---

### Post by c.monty on 2013-07-10
Hi!

I've created a low-level backup of the "damaged disk" to exactly the same disk (same product, same size) using ddrescue, and the following data is taken from the copy.

The "verify disk" option of gdisk returns this:
```
Expert command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 3907073134 sectors, needs to be 5860533168 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: partition 1 is too big for the disk.

Identified 4 problems!

```

Option "show detailed information (...)" returns this:
```

Command (? for help): i
Using 1
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: 37786D32-C98F-4624-9440-94F79BE79793
First sector: 2048 (at 1024.0 KiB)
Last sector: 5860533134 (at 2.7 TiB)
Partition size: 5860531087 sectors (2.7 TiB)
Attribute flags: 0000000000000000
Partition name: 'Linux filesystem'

```

According to this the last section of the disk is 5860533134.
The output of gdisk -l returns: First usable sector is 34, last usable sector is 5860533134.
And the problem says: Disk size is 3907073134 sectors, needs to be 5860533168 sectors.

This would imply that data allocates more sectors on that disk that are available. Or not?
However, I don't think that I put more than 2.5TB of data on the disk.

---

### Post by oldfred on 2013-07-10
I think something with fdisk or other tools not gpt or 3TB drive aware may have made drive too small. Drive size should be larger than useable size as partition table at front and end of drive use some sectors. Linux also reserves 5% which if just a data disk you may want to adjust down. When drives were small 5% reserved enough to prevent drive filling and crashing, but 5% of 3TB is too much.

       Also in Linux the default is to reserve 5% of the diskspace for the superuser (this can be adjusted using tune2fs -m).
Info on partition:
sudo tune2fs -l /dev/sda1

---

### Post by c.monty on 2013-07-10
The output of sudo tune2fs -l /dev/sdh1 says:
Can't find valid filesystem superblock

How can I repair the partition?

---

### Post by oldfred on 2013-07-10
If you have run the gdisk repairs then you may need to run fsck. Reconfirm that is still is mounted at sdh1.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdh1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdh1
#if errors: -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdh1

---

### Post by c.monty on 2013-07-11
Hi!

I didn't run any repair tasks with gdisk, because I'm not sure which option I should use.
I have still problems to understand what the potential root cause is.

By the way, the partition is formatted with XFS, and with the current damaged status I cannot mount it.
However, there are many websites providing information to repair a XFS partition, e.g. [this one]("http://docs.cray.com/books/S-2377-22/html-S-2377-22/z1029470303.html").

THX

---

### Post by oldfred on 2013-07-11
I do not know about XFS as that does need different tools to fix. 
But the gdisk repairs still should be run to update partition tables. Maybe even just loading and issuing the w command to write updates? Have not had to repair my gpt drives.

---

### Post by c.monty on 2013-07-12
> **oldfred said:**
> Use gdisks commands to update backup gpt partition table.

 repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

Understood... what are the command options to "update backup gpt partition table"?

Would the following approach work?
Reading all data from the start sector 2048 to the end sector 3907073100 and writing this data to a partitioned backup disk.

---

### Post by oldfred on 2013-07-12
Did you install:
  xfsprogs needed for xfs partitions, new install may not add, or liveCD may not have?

Backing up partition table is just the partition table, none of the data. You probably do not want to just copy entire 3TB as much of that should be empty space?

---

### Post by c.monty on 2013-07-12
1. I'm using live CD Knoppix including all tools required. If any tool is missing I could install it.
2. Trying some recovery options of gdisk failed when I wanted to "write table to disk and exit" with option w.
3. Continuing this try&error for repairing with these 2 steps: deleting existing partition, creating new partition with start sector 2048 and end sector 3907073100 representing a 2TB partition (on a 3TB HDD).
4. Now I can mount the partition, but no data is found.

Does this mean, the creation of a new partition deleted all data? I guess not, and I'm trying to recover the data using "testdisk".

If feasible, I would copy all data from the source HDD to a backup HDD (I have two identical HDDs WD30EZRX, same type, same size). Please provide instructions for copying all data.

Here's some output of the current disk settings:
```
knoppix@Microknoppix:~$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): i
Using 1
Partition GUID code: 0FC63DAF-8483-4772-8E79-3D69D8477DE4 (Linux filesystem)
Partition unique GUID: AF3E2091-099F-4A31-BC1F-16C3F7B16ED5
First sector: 2048 (at 1024.0 KiB)
Last sector: 3907073100 (at 1.8 TiB)
Partition size: 3907071053 sectors (1.8 TiB)
Attribute flags: 0000000000000000
Partition name: 'Linux filesystem'

Command (? for help): v

No problems found. 2014 free sectors (1007.0 KiB) available in 1
segments, the largest of which is 2014 (1007.0 KiB) in size.

```

---

### Post by oldfred on 2013-07-12
If you created the new with same start and end all the data should be there. 

 If partition cannot be mounted and data shown, then only way to recover some data is with photorec which is part of testdisk. Not sure if it works with XFS or not. Photorec just scans a drive for anything that looks like a file, you can restrict it to only look for certain file types. But that does not speed it up. It may take literately days with a 3TB drive as it is a very low level scan.

Was there some reason for XFS?
 Ubuntu 12.04 LTS - Benchmarking All The Linux File-Systems
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1204_fs&num=1)
Large HDD/SSD Linux 2.6.38 File-System Comparison: EXT3, EXT4, Btrfs, XFS, JFS, ReiserFS, NILFS2
[http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1](http://www.phoronix.com/scan.php?page=article&item=linux_2638_large&num=1)

 
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

      
 Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by c.monty on 2013-07-12
Since my last posting, Testdisk is running on the low-level copy HDD.
The original HDD is still untouched.

I'll wait and see if Testdisk can recover any data. By the way, there will be only stream-files *.ts stored on the HDD, nothing else.
Anyway, as long as Testdisk is running, I cannot mount the partition.

Do I understand you correctly: 
If the new partition is equal to the original, then I should be able to mount the partition and read all data?

Why did I use XFS?
Well, I thought it's the best option for my usage: storage of recording files with file size 3-15GB.
Actually, this [article]("http://www.mythtv.org/wiki/XFS_Filesystem") convinced me of using this format.

---

### Post by oldfred on 2013-07-12
I do not know about XFS, but the article seems to compare it more with ext3, or it may be dated. Ubuntu standardized on ext4 with 9.10. It did have a few issues back then, but nothing more than any other system recently. 
The Phoronix articles are more current, but I do not think they just test for larger files only which some file systems like XFS may be better.

---

