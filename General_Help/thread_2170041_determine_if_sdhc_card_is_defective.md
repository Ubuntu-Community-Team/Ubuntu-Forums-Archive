---
title: "determine if sdhc card is defective"
date: 2013-08-24
forum: General Help
---

### Post by msousa on 2013-08-24
Hi

I have a 4GB sdhc card (with two partitions) that when I plug into my ubuntu 12.04 laptop one of the partitions gets mounted but the other generates an error popup that says:

Unable to mount 3.9 GB Filesystem
Error mounting: mount: block device /dev/sdc2 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sdc2,


This is what df -h gives:
$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda1       226G   26G  189G  13% /
udev            1.8G  4.0K  1.8G   1% /dev
tmpfs           741M  872K  740M   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            1.9G  396K  1.9G   1% /run/shm
/dev/sdc1       118M  8.9M  109M   8% /media/ESCBOS2009
$

One of the partitions shows up as sdc1 but the other partition does not.
In Nautilus (3.4.3), it shows the defective partition but it gives the same error as above when trying to click into it.

I've tried deleting the partitions with fdisk but those attempts have failed. I have also click the r/w switch on the sd card to see if that improves things but nothing changed.

Are there tools available in ubuntu to check if this is a defective sd card?

Thanks...

Mike

---

### Post by msousa on 2013-08-25
A little more info. The SD Card has two partitions (sdc1, sdc2) on it.  One of them (sdc1) is viewable. Below is the output of fsck on each  partition.

```

$ sudo fsck -rv /dev/sdc1
fsck from util-linux 2.20.1
dosfsck 3.0.12 (29 Oct 2011)
dosfsck 3.0.12, 29 Oct 2011, FAT32, LFN
Checking we can access the last sector of the filesystem
Boot sector contents:
System ID "mkdosfs"
Media byte 0xf8 (hard disk)
       512 bytes per logical sector
      2048 bytes per cluster
         1 reserved sector
First FAT starts at byte 512 (sector 1)
         2 FATs, 16 bit entries
    120320 bytes per FAT (= 235 sectors)
Root directory starts at byte 241152 (sector 471)
       512 root directory entries
Data area starts at byte 257536 (sector 503)
     60102 data clusters (123088896 bytes)
16 sectors/track, 4 heads
         0 hidden sectors
    240912 sectors total
Checking for unused clusters.
/dev/sdc1: 29 files, 4556/60102 clusters
$
$
$ sudo fsck -rv /dev/sdc2
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
fsck.ext3: Read-only file system while trying to open /dev/sdc2
Disk write-protected; use the -n option to do a read-only
check of the device.
$ 
$ sudo fsck -nv /dev/sdc2
fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
Warning: skipping journal recovery because doing a read-only filesystem check.
/dev/sdc2 has been mounted 39 times without being checked, check forced.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Free blocks count wrong (455729, counted=455727).
Fix? no

Free inodes count wrong (426968, counted=426967).
Fix? no


/dev/sdc2: ********** WARNING: Filesystem still has errors **********


   46312 inodes used (9.79%)
     350 non-contiguous files (0.8%)
      32 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 1888/37/0
  490097 blocks used (51.82%)
       0 bad blocks
       1 large file

   37930 regular files
    3749 directories
      31 character device files
      40 block device files
       1 fifo
       0 links
    4553 symbolic links (4546 fast symbolic links)
       0 sockets
--------
   46304 files
$

```

---

### Post by Wim Sturkenboom on 2013-08-25
You can use the _dd_ command to wipe the MBR and partition table. After that you should be able to partition and format. Use your favorite search engine :) Result e.g. [http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/](http://www.linuxquestions.org/questions/linux-newbie-8/using-dd-to-zero-the-mbr-query-606489/)

And there is the _badblocks_ command to check your card.

---

### Post by msousa on 2013-08-25
I have even more info, this time from fdisk:

```

$ sudo fdisk /dev/sdc
You will not be able to write the partition table.

Command (m for help): p

Disk /dev/sdc: 3999 MB, 3999268864 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63      240974      120456    c  W95 FAT32 (LBA)
/dev/sdc2          240975     7807589     3783307+  83  Linux

Command (m for help): d
Partition number (1-4): 1

Command (m for help): d
Selected partition 2

Command (m for help): p

Disk /dev/sdc: 3999 MB, 3999268864 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System

Command (m for help): w
fdisk: unable to write /dev/sdc: Bad file descriptor
$ 

```


Can the 'Bad file descriptor' be fixed? This is starting to look to me that the SD Card is hosed:(. I'd like to be sure...

---

### Post by msousa on 2013-08-25
I've tried completely wiping out everything on the card

```

~$ tr '\000' '\377' < /dev/zero > /dev/sdc
bash: /dev/sdc: Permission denied
$
$
$ dd if=/dev/zero of=/dev/sdc
dd: opening `/dev/sdc': Permission denied
$ dd if=/dev/zero of=/dev/sdc1
dd: opening `/dev/sdc1': Permission denied
$ dd if=/dev/zero of=/dev/sdc2
dd: opening `/dev/sdc2': Permission denied
$

```

still no luck :(:confused:

---

### Post by tgalati4 on 2013-08-25
Use the *sudo* in front of your formatting commands.

---

