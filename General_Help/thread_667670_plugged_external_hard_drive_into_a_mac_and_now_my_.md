---
title: "plugged external hard drive into a mac and now my ext3 filesystem is broken"
date: 2008-01-14
forum: General Help
---

### Post by ycason on 2008-01-14
The Title describes the problem.  I plugged it into the mac which told me it couldn't mount the filesystem.  Then when I tried to plug it back into my linux laptop it says that the space on the external hard drive is unformatted.  

I've tried fsck and this is all I get:

fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
Couldn't find ext2 superblock, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdb

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>


Please help me!! :(

---

### Post by articpenguin on 2008-01-14
hi 

post your fdisk

> sudo fdisk -l

---

### Post by smartboyathome on 2008-01-14
Install GParted from the repositories and look at your external hard drive. Is it unformatted? If so, I hope you backed your stuff up.

---

### Post by articpenguin on 2008-01-14
seems its a superblock issue i will look into this.

---

### Post by ycason on 2008-01-14
sudo fdisk -l /dev/sdb

Disk /dev/sdb: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00c3f475

Disk /dev/sdb doesn't contain a valid partition table

---

### Post by ycason on 2008-01-14
I found a utility called TestDisk.  I'm going to try it out now and see if it can do anything for me.

TestDisk Website:  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)



Edit: it hasn't found my partition, so any suggestions would be helpful

---

### Post by ycason on 2008-01-14
There was only the one ext3 partition on the drive if that helps.  What would the sector size parameter be for the hard drive?

---

### Post by ycason on 2008-01-14
*bump*

---

### Post by articpenguin on 2008-01-14
i think your in trouble =(. Your external disk dosent have a valid partition table so i think its lost.

---

