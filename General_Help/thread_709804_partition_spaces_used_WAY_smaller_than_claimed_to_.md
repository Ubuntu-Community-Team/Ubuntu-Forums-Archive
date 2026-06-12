---
title: "/ partition spaces used WAY smaller than claimed to be used"
date: 2008-02-27
forum: General Help
---

### Post by buckminster on 2008-02-27
I just noticed that my / (/dev/hda1) partition is claiming to use 9.2 GB when two days ago it was only using less than 5 GB two days ago. I also noticed my automated backups (using Simple Backup Config) didn't run the last two days. When I run Disk Usage analyzer on the partition, it only shows 3.3 GB of stuff.

I booted to a LiveCD and ran the check option in gparted it didn't fix the problem (I don't know enough about the output to understand what it did find). I also manually ran fsck on the partition. This was the output:

```
ubuntu@ubuntu:~$ sudo fsck.ext3 -fv /dev/hda1
e2fsck 1.40.2 (12-Jul-2007)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

  138827 inodes used (1.96%)
    2799 non-contiguous inodes (2.0%)
         # of inodes with ind/dind/tind blocks: 7389/78/1
 2652198 blocks used (18.58%)
       0 bad blocks
       2 large files

  111328 regular files
   13126 directories
     132 character device files
      26 block device files
       2 fifos
     490 links
   14190 symbolic links (12310 fast symbolic links)
      14 sockets
--------
  139308 files

```

I don't see any obvious messages relating to this in the logs, but obviously something is wrong. Any suggestions on commands to run figure out and/or fix what is going on? Running Gutsy with all of the latest updates.

Thanks!

Nevermind, my external backup drive must not have been plugged in once when it was going to do back up so it created the folder on the root partition under /media/<external drive>, Hi ho.

---

