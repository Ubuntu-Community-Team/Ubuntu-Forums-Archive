---
title: "Partitioning problems.. 2days and rising"
date: 2008-05-20
forum: General Help
---

### Post by Der_Idiot on 2008-05-20
Okay, basicall I just went server 2003 to Ubuntu server. All drives were NTFS. I copied data off the drives, and moved them to primary drive, and cfdisk'd them to ext3 (delete, create, primary, all space, and changed type to 83, than wrote).

Here's the fun part. I have 2x Promise Ultra133 TX2's in my system for added IDE support (I have 7 drives). Two of my drives are on the on-board ide slot. Five others are on the IDE controllers.
All data moved off them fine, no corruption. All data moved back, same.

Basically, I have a folder on /dev/sdg1 that gives invalid i/o error. I tried rm -rf, I tried renaming it, moving it, removing and replacing the partition. I can't think of anything else. I also did fsck and e2fsck and got back superblock (for another drive that doesnt give invalid i/o too..?). Am I missing a driver or something?


```
shadowfax@Behemoth:/shared/j-drive/mp3$ ls -l
ls: cannot access {Rock}: Input/output error
total 0
d????????? ? ? ? ?                ? {Rock}
```


```
shadowfax@Behemoth:~$ sudo fsck /dev/sdg
fsck 1.40.8 (13-Mar-2008)
e2fsck 1.40.8 (13-Mar-2008)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdg

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

```

I get the same message with e2fsck.

I cfdisk'd and made a logical partition, then deleted, and created a primary, and get this now:
```
shadowfax@Behemoth:~$ sudo mount /dev/sdg1 /shared/j-drive/
mount: you must specify the filesystem type
```


Anyone have ANY ideas? :(

---

### Post by Der_Idiot on 2008-05-20
I ended up re-partitioning half the drives after moving the data one more time. Somehow I mixed up my partitioning scheme and didn't actually put the file system on the drives (h, i, j) thus resulting in the stated problem. It just so happens that the power outage caused the mp3's dir issue.

All is fixed (I think). I'll post back if anything else is broken ):P

---

