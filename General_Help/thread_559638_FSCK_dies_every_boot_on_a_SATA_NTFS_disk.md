---
title: "FSCK dies every boot on a SATA NTFS disk"
date: 2007-09-25
forum: General Help
---

### Post by aaargh486 on 2007-09-25
Everytime I boot I get this message:

```
Log of fsck -C -R -A -a 
Tue Sep 25 18:04:15 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda2
/dev/sda2: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

/dev/hda1: clean, 32/24096 files, 25610/96356 blocks
fsck died with exit status 8

Tue Sep 25 18:04:15 2007
----------------

```

It then says something about this text being written to /var/log/fsck/checkfs and ask me to either open a maintenance shell or press ctrl-D, what I do every single time.

It doesn't really surprise me it dies, because those drives are both NTFS drives. What I think is strange is that I manually set this drives not to check in fstab. Here are the contents of my /etc/fstab

```
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda3
UUID=e2c99a25-1cad-464a-8477-b2aa9630d98a /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=9b172065-95ab-42a4-948a-ae430e298538 /boot           ext3    defaults        0       2
# /dev/hda2
UUID=034e2c0d-1093-4ef7-9610-db4312ae6b35 /home           ext3    defaults        0       2
# /dev/hda4
UUID=abc91d8e-9116-453a-a8c6-985cd05d936f none            swap    sw              0       0


#/dev/sda1
/dev/sda1       /media/SYSTEM   ntfs-3g         auto,users,uid=1000,gid=1000   0 0
#/dev/sda2
/dev/sda2       /media/DATA     ntfs-3g         auto,users,uid=1000,gid=1000   0 0

```

It's not rampant because the disks are fine and everuthing boots well, but it's really really annoying. The disks are completely without faults, I booted back to Windows several times in a row and shut down correctly and nothing ever changed.

Can anybody help me?

Lots of Thanks in advance,

Kasper

---

### Post by aaargh486 on 2007-09-26
No one? Please, it's driving me crazy! It's gotta have a simple solution, it looks like such a simple problem.

---

### Post by fjgaude on 2007-09-26
I've never seen this before. The only thing I can suggest is to do a tune2fs on the two ntfs drive, one partition at a time:

```
sudo tune2fs -c 0 /dev/sda[1,2]
```

Let us know what happens, if anything.

---

### Post by dabl on 2007-09-26
I have not seen this one before either, and I run a NTFS thumb drive (memory stick), and I used to run a normal NTFS partition on a hard drive.

But, I would be seriously concerned because of the source of the error message: fsck.**ext3**

I'm not sure the problem is the NTFS drives themselves, really, although it is pointing to them.  It almost looks to me like the super-block on the root filesystem partition has some bad poop in it, which is a bad thing for your system, not just the NTFS drives.  :confused:

---

### Post by LauraSakura on 2007-09-26
I don't have any NTFS partitions on my drive anymore (it was NTFS originally though, now its all ext3 except the swap) and I get somethign similar every time that I boot. FSCK errors and trying to start recovery console. Then it says things like "apt-get not installed type apt-get install apt" but if I press Ctrl-D it boots and everything runs ok. Its strange.

---

### Post by dabl on 2007-09-26
> **LauraSakura said:**
> 

Then it says things like "apt-get not installed type apt-get install apt" but if I press Ctrl-D it boots and everything runs ok. 

That one I HAVE seen.  I believe there is a mis-match between your /etc/fstab drive/partition designations, and your /boot/grub/menu.lst drive IDs, or possibly an error between 2 lines within the menu.lst file.  Bearing in mind the difference in their drive-naming conventions, you need to compare them side by side, and let /etc/fstab be the "expert" -- i.e. change menu.lst to match fstab, not the other way.

For example, if the second line in the "Automagic Kernels" stanza of menu.lst says (hd1), and the third line has a UUID that is actually /dev/sda, that's a big problem, because /dev/sda is hd0 in Grub-speak, not hd1.

Hope this helps you sort it out!  :)

---

### Post by aaargh486 on 2007-09-27
> **fjgaude said:**
> I've never seen this before. The only thing I can suggest is to do a tune2fs on the two ntfs drive, one partition at a time:

```
sudo tune2fs -c 0 /dev/sda[1,2]
```

Let us know what happens, if anything.

```
aaargh486@SPHERE:~$ sudo tune2fs -c 0 /dev/sda1
Password:
tune2fs 1.40-WIP (14-Nov-2006)
tune2fs: Bad magic number in super-block while trying to open /dev/sda1
Couldn't find valid filesystem superblock.
aaargh486@SPHERE:~$ 

```

Too bad, but thanks anyway.

I've changed something in my device.map. Maybe it helps, maybe it breaks everything. We'll see.

---

### Post by LauraSakura on 2007-09-28
> 
That one I HAVE seen. I believe there is a mis-match between your /etc/fstab drive/partition designations, and your /boot/grub/menu.lst drive IDs, or possibly an error between 2 lines within the menu.lst file. Bearing in mind the difference in their drive-naming conventions, you need to compare them side by side, and let /etc/fstab be the "expert" -- i.e. change menu.lst to match fstab, not the other way.

yeah, thats what happened. MEPIS and Ubuntu had different UUID's for the same partitions in their /etc/fstab. Matched everything up to blkid, and it boots fine now. Thanks :)

---

