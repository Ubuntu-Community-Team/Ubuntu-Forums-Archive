---
title: "cannot mount ext3 partition - superblock error"
date: 2008-02-07
forum: General Help
---

### Post by Kamiyay on 2008-02-07
Well I moved all of my music to this drive. 40 GB of it. So I kinda want to be able to access this again.

The drive/partition wont mount.

gparted gives me

Couldn't find valid filesystem superblock
dumpe2fs: Attepmt to read block from filesystem resulted in a short read while trying to open /dev/hdd1

fsck -f on /dev/hdd gives this:

Couldn't find ext2 superblock, trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/hdd

So with the power of google I tried figuring this out. I don't really know what I am doing.

fdisk -l sees the drive

None of the alternate superblocks work. (as found via testdisk)

All I want is to be able to recover the music I had on this drive. Please help me.

---

### Post by kevstar31 on 2008-02-07
try the instructions here:
[http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/](http://edseek.com/archives/2004/02/25/ext3-filesystem-bad-superblock-recovery/)

---

### Post by Kamiyay on 2008-02-07
umm... I totally did that wrong and it erased the drive....

Oh well i guess... Unless there is a way to recover that even...

---

### Post by kevstar31 on 2008-02-08
what commands did you use?

---

