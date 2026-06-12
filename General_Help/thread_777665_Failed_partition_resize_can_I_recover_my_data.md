---
title: "Failed partition resize: can I recover my data?"
date: 2008-05-01
forum: General Help
---

### Post by Daan on 2008-05-01
Hello,

During the process of resizing a partition with gparted, I got an error:

```
check filesystem on /dev/sdb2 for errors and (if possible) fix them  00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sdb2
     	
/dev/sdb2 is mounted.
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Cannot continue, aborting.
```

apparently causing me to loose the data that was on the partition.

The problem was that Ubuntu or Gnome had automatically mounted the partition sdb2, which is on a hard disk which is hooked up through usb. I now have one small partition and a lot of unallocated space on the drive. I meant to have one big partition with the data from the small partition on it, but it seems gone now! The device can be mounted but appears to be empty. However, gparted says 79% of the partition is in use.

Can I recover the data?

Maybe I should run the command **e2fsck -f -y -v /dev/sdb2** again but without the partition mounted?

Here's the entire gparted_details.htm:

```
GParted 0.3.3

Libparted 1.7.1

Delete /dev/sdb3 (ext3, 87.48 GiB) from /dev/sdb  00:00    ( SUCCES )
     	
calibrate /dev/sdb3  00:00    ( SUCCES )
     	
path: /dev/sdb3
start: 58589055
end: 242051354
size: 183462300 (87.48 GiB)
delete partition  00:00    ( SUCCES )

========================================

Delete /dev/sdb1 (ext3, 27.94 GiB) from /dev/sdb  00:00    ( SUCCES )
     	
calibrate /dev/sdb1  00:00    ( SUCCES )
     	
path: /dev/sdb1
start: 63
end: 58589054
size: 58588992 (27.94 GiB)
delete partition  00:00    ( SUCCES )

========================================

Grow /dev/sdb2 from 74.50 GiB to 189.92 GiB  02:46:03    ( ERROR )
     	
calibrate /dev/sdb2  00:00    ( SUCCES )
     	
path: /dev/sdb2
start: 242051355
end: 398283479
size: 156232125 (74.50 GiB)
calculate new size and position of /dev/sdb2  00:01    ( SUCCES )
     	
requested start: 0
requested end: 398283479
requested size: 398283480 (189.92 GiB)
new start: 63
new end: 398283479
new size: 398283417 (189.92 GiB)
check filesystem on /dev/sdb2 for errors and (if possible) fix them  03:51    ( SUCCES )
     	
e2fsck -f -y -v /dev/sdb2
     	
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

44050 inodes used (0.45%)
666 non-contiguous inodes (1.5%)
# of inodes with ind/dind/tind blocks: 19439/783/0
15405595 blocks used (78.89%)
0 bad blocks
1 large file

43834 regular files
207 directories
0 character device files
0 block device files
0 fifos
0 links
0 symbolic links (0 fast symbolic links)
0 sockets
--------
44041 files
e2fsck 1.40.2 (12-Jul-2007)
move partition to the left  00:01    ( SUCCES )
     	
old start: 242051355
old end: 398283479
old size: 156232125 (74.50 GiB)
new start: 63
new end: 156232187
new size: 156232125 (74.50 GiB)
move filesystem to the left  02:42:10    ( SUCCES )
     	
using internal algorithm
copy 156232125 sectors
finding optimal blocksize
     	
copy 32768 sectors using a blocksize of 64 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.32211 seconds
copy 32768 sectors using a blocksize of 128 sectors  00:02    ( SUCCES )
     	
32768 of 32768 copied
2.48633 seconds
optimal blocksize is 64 sectors (32.00 KiB)
copy 156166589 sectors using a blocksize of 64 sectors  02:42:06    ( SUCCES )
     	
156166589 of 156166589 copied
156232125 sectors copied
check filesystem on /dev/sdb2 for errors and (if possible) fix them  00:00    ( ERROR )
     	
e2fsck -f -y -v /dev/sdb2
     	
/dev/sdb2 is mounted.
e2fsck 1.40.2 (12-Jul-2007)
e2fsck: Cannot continue, aborting.



========================================
```

---

### Post by forrestcupp on 2008-05-01
This is why we always say to backup before messing with partitions.  I'd say you're probably screwed, unless you want to hire a computer forensic expert or something.

---

### Post by Daan on 2008-05-01
> **forrestcupp said:**
> This is why we always say to backup before messing with partitions. 

I backed up as much as I could but was short on storage space. :(

---

### Post by Daan on 2008-05-03
Just in case anyone wants to know:

I got my data back using testdisk running from the PartedMagic live CD.

---

### Post by ben2talk on 2008-10-16
I have a slightly different problem.

Before I started, looking with Gparted, I had (320GB)
30GB xp partition
then an extended sda3 partition. Inside this was swap(4GB) and root (200GB)
To finish the disk, I had an XFS partition (used mostly for ISO's of DVD's I wanted to split and copy).

I kept most of my personal stuff on Sdb - but there's still 6 months of tuning on that 200GB partition (and quite a lot of personall pictures I hadn't yet backed up!)

Mission - put swap on SDB.
Part 1, copy all filees from Sdb2 (ext3) to sdb1 (NTFS shared) in a backup folder. then resize sdb2 and put a swap after. 
No problem!

Mission 2 - delete swap, extend the root partition to fill the space.
For some reason, when I went to make a drink, Gparted exited. I started it and checked - seems fine. The ubuntu partition is there, but on it is only one 'lost+found' folder! Where has my tree gone?
I have a very slow internet connection (fastest download 20kb/s, often around 10 or less!) and so I don't want to start all over again!

What can I do?

---

### Post by bodhi.zazen on 2008-10-16
You can try testdisk and photorec (both are in the repos).

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

IMO you are best off working from a live CD.

---

### Post by ben2talk on 2008-10-16
The root partition was moved, testdisk shows it has no problems - the issue for me is that it was wiped clean too!:(

> **bodhi.zazen said:**
> You can try testdisk and photorec (both are in the repos).

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

IMO you are best off working from a live CD.

---

### Post by bodhi.zazen on 2008-10-16
> **ben2talk said:**
> The root partition was moved, testdisk shows it has no problems - the issue for me is that it was wiped clean too!:(

That is what Photorec is for, recovering lost files (testdisk recovers partitions).

If Photorec cannot help I advise professional consultation.

---

