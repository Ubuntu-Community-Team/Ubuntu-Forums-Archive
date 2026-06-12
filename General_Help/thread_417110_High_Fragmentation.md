---
title: "High Fragmentation"
date: 2007-04-21
forum: General Help
---

### Post by ahaslam on 2007-04-21
Hi there, I find this very weird:

```
root[~]# umount /dev/sda3
root[~]# e2fsck -fv /dev/sda3
e2fsck 1.38 (30-Jun-2005)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

    7375 inodes used (0%)
    1524 non-contiguous inodes (20.7%)
         # of inodes with ind/dind/tind blocks: 952/304/1
 5086043 blocks used (15%)
       0 bad blocks
       1 large file

    6935 regular files
     409 directories
       0 character device files
       0 block device files
       0 fifos
       0 links
      21 symbolic links (21 fast symbolic links)
       1 socket
--------
    7366 files
```

Am I reading that right, only used 15% but it's 20% fragmented?

I don't usually use ext3, it's only being used on this single partition. The last time I used it I only got high fragmentation when the drive became close to full, not at 15%. I'm assuming ext3 doesn't offer a defrag tool like xfs_fsr or e2defrag unless you temporarily down grade to ext2?

Anyway it seems high, anyone else experience this?

---

### Post by jrusso2 on 2007-04-21
From my understanding of fragmentation in ext3 is that yes you can defrag it if you downgrade to ext 2 first.

But that the fragmentation does not effect performance.  It seems the way that Linux file systems work would be considered fragmentation in other file systems due to it not being contiguous.  But that this is normal and does not effect performance.

---

### Post by aidanr on 2007-04-21
yep, i've also got high fragmentation on both my ide drives and low fragmentation on my sata drive after updating to feisty

with edgy it was always about 5%, now its 20-25% and 0.5% on the sata

although i did move about quite an amount of stuff preparing for the fesity install

---

### Post by ahaslam on 2007-04-21
This is on a SATA drive. XFS doesn't show such fragmentation & provides a simple defrag tool.
I suppose this is my way of saying that ext3 sucks...

---

### Post by psusi on 2007-04-23
You don't have to downgrade to ext2, just install the defrag package ( in universe ) and run it on the partition.  Also that number from fsck can be misleading.  It says 20% of the files on the partition have more than one extent.  If they are large ( several or more MB ) files and only have 2-3 extents each, that really isn't anything to worry about.

---

