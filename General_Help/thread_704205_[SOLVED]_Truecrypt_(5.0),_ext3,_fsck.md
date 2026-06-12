---
title: "[SOLVED] Truecrypt (5.0), ext3, fsck"
date: 2008-02-22
forum: General Help
---

### Post by wieman01 on 2008-02-22
Pretty much sums up what I need to know... I have a dedicated encrypted partition for my personal data... let's say:
> /dev/sda2
It's an **ext3** file system and now I ask myself the question if I have to run **'e2fsck'** manually from time to time. Of course the encrypted volume is not mounted upon boot, so there is not system-forced check. 

Any ideas?

Nevertheless I have tried to run **'e2fsck'** but I keep getting this error message:
> e2fsck 1.40-WIP (14-Nov-2006)
e2fsck: Bad magic number in super-block while trying to open /dev/sda2

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

It does not make much sense to me. 

Again anybody? Advice is much appreciated.

---

### Post by Magnes on 2008-02-22
I did manually run e3fsck with a success on a  truecrypt ext3 volume once. It's probably important to do so from time to time. I don't remember exactly how I made it.
Probably (but I'm not sure and can't test it at work):
1. Run truecrypt on the partition.
2. Unmount it (sudo unmount /media/yourpartition).
3. Run e2fsck on a virtual device (/dev/loop0 or sth like that) made by truecrypt (it can be listed with truecrypt -l) - not on the /dev/sda2!.

---

### Post by wieman01 on 2008-02-22
Thanks for your reply first of all. I did that. Basically I followed this post:

[http://ubuntuforums.org/showpost.php?p=1908538&postcount=8]("http://ubuntuforums.org/showpost.php?p=1908538&postcount=8")

But then I encounter that error message and I have no idea what I am supposed to do... :-(

---

### Post by wieman01 on 2008-02-23
I need to bump this up once more... Sorry.

---

### Post by wieman01 on 2008-02-29
Last desperate bump...

---

### Post by wieman01 on 2008-03-05
OK, last post before I close this thread. I have reverted to using FAT32 rather than EXT3. Reasons being:

A. This error message kept popping up without me being able to 'fsck' my partition.
B. Automatic EXT3 fsck is impossible since it's an encrypted partition.
C. Hence I don't trust an EXT3 file system that is not regularly fs-checked and maintained.

So FAT32 it is. I don't really mind much because the encrypted partition only stores data pertaining to a single user. I don't really need EXT3 under the circumstances.

In case anybody is interested and is watching this thread...

---

### Post by wieman01 on 2008-03-16
Now I went back and reformated the drive ("ext3"), ran "e2fsck" after umounting it and having remounted it, and everything seemed fine. No more error messages.

FAT32 turned out to be a pain because Slimserver would recognize music folders residing on a FAT32 volume. Same with Unison which refused to synchronize my emails. "ext3" was the only option so I went through the pain of formating and copy GBs of data. It's fine now.

---

