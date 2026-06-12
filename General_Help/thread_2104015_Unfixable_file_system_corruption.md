---
title: "Unfixable file system corruption"
date: 2013-01-11
forum: General Help
---

### Post by FishLeg on 2013-01-11
**Intro**
So I added a nice 3TB drive to my 1TB and 2TB drives in my file server. I decided to create a 2TB RAID1 using the old 2TB drive and a 2TB partition on the new 3TB drive. Use RAID1, they said. It protects you from disk failures, they said. So what did I do:
Run badblocks on the new 3TB drive for twice (took more than two days. No errors)
create GPT on **3TB** drive. Create **2TB** partition in it.
Create RAID1 with one drive missing. (degraded mode)
Create encrypted volume on md0 using cryptsetup/luks
Format the encrypted volume using ext4
Copy all the stuff from the old 2TB drive to the new encrypted degraded raid1.
Create a GPT on the old 2TB drive, create a partition of exactly the same size as the one on the 3TB drive.
Add that one to the RAID1, rebuild starts...
Everything looks fine at first...

**The problem**
After the first reboot, I decrypted and mounted the new RAID1 ext4 partition again... Surprise surprise, doing a *ls*, I got some Input/Output errors, and the flags of some directories shows up ad something like ?-------- ?------.
Oh great, some data corruption. On a RAID1. so first thing I did was check the smart values of the drives; both are OK, no pending or reallocated sectors. So maybe really just a coincidence and the fs got messed up. So I try to run fsck.ext4... It scans, finds lots of problems, inodes with invalid values, shared inodes between files, cr*p like that.
The problem now is that I can't fix everything. After a while, fsck locks up, using 100% on one core, nothing happens for hours.
Also, I get some messages I do not really understand:
> root@schublade:/mnt# fsck.ext4 -f -v /dev/mapper/tb2
e2fsck 1.42.5 (29-Jul-2012)
Pass 1: Checking inodes, blocks, and sizes
Error reading block 53988175297502 (Invalid argument).  Ignore error<y>? yes
Force rewrite<y>? no

Running additional passes to resolve blocks claimed by more than one inode...
Pass 1B: Rescanning for multiply-claimed blocks
Multiply-claimed block(s) in inode 7: 328 563 787
Illegal block number passed to ext2fs_test_block_bitmap #4119209389 for multiply claimed block map
Illegal block number passed to ext2fs_test_block_bitmap #3601002943 for multiply claimed block map
[lots of those]
Illegal block number passed to ext2fs_test_block_bitmap #3313372385 for multiply claimed block map
Pass 1C: Scanning directories for inodes with multiply-claimed blocks
Pass 1D: Reconciling multiply-claimed blocks
(There are 41 inodes containing multiply-claimed blocks.)

File /some/file (inode #24903817, mod time Fri Jan  4 17:33:20 2013)
  has 1 multiply-claimed block(s), shared with 1 file(s):
        /some/directory (inode #59506689, mod time Sat Jan  5 04:39:14 2013)
Clone multiply-claimed blocks<y>? yes
[100% cpu usage]

So... How do I fix an unfixable file system, or can I just forget all my data? Only thing I can think of is buy yet another drive to copy everything that's left to, and get rid of that mess.

Also
> Error reading block 53988175297502 (Invalid argument).
that block number would mean that the volume is some hundred terabytes large, if I'm not mistaken. Why doesn't fsck notice that?

---

### Post by FishLeg on 2013-01-12
Aight so I read somewhere that pass 1D could require a ton of memory. The box only had 1GB installed, and htop revealed that all of the memory was in use. So I stuffed 4GB into that box and rerun, fsck now occupied about 2,5GB. I waited over night, and in the end it aborted with something like "Illegal double indirect inode"
Rerun it about two times and got the same result, then eventually it finished. Had to run it two more times until no more errors would be found.
Now I got a pretty fancy file system there:
```
       66574 inodes used (0.05%, out of 122093568)
        1021 non-contiguous files (1.5%)
          42 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 1/1/1
             Extent depth histogram: 65730/773
   427428797 blocks used (87.53%, out of 488344272)
           0 bad blocks
         109 large files

       63891 regular files
        2647 directories
           3 character device files
           7 block device files
          11 fifos
  4294967287 links
           0 symbolic links (0 fast symbolic links)
           9 sockets
------------
       66421 files
```

I like the link count really.
There is just a big load of **** now if I mount the FS. It actually looked more intact before I tried fsck.

Lesson learned: Do a backup *before* trying to fix things with fsck.

---

