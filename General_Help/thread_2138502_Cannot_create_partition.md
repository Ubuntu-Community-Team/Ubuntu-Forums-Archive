---
title: "Cannot create partition"
date: 2013-04-24
forum: General Help
---

### Post by mirzar on 2013-04-24
Hi

I connected a new internal HDD to my headless ubuntu server and would  like to partition it so I can copy my existing system disk to it (the  existing disk is way low on free space and the new disk is larger.)

The disk shows in /dev/sdd (there is not sdd1 or any partitions  showing).  Yet the new disk does not show up using fdisk -l  and  attempts to mount keep referring to fstab.

```

tom@HouseMedia:/$ mount /dev/sdd mount: can't find /dev/sdd in /etc/fstab or /etc/mtab tom@HouseMedia:/$ mount /dev/sdd1 mount: can't find /dev/sdd1 in /etc/fstab or /etc/mtab
```

I had previously mounted and partition this drive but after using dd to  restore a disk image of my existing system disk, the new disk was still  empty.  I'm a little lost on what exactly is wrong and would appreciate  some help on getting back to square one again!

(I have downloaded the **Ubuntu** from this site:[ &#1605;&#1607;&#1585;&#1711;&#1575;&#1606;]("http://japalaghi.com") )

Thank for your help.

---

### Post by r.stiltskin on 2013-04-24
It seems that something went wrong with your use of dd.

The messages about /etc/fstab and /etc/mtab aren't surprising or useful.  Those are files on your old disk, and unless you explicitly made changes to those files there's no reason to expect anything about the new disk to appear there.

If fdisk -l doesn't list anything for sdd, there must be no partition table to list.  Probably, whatever you did with your dd command overwrote the partition table that you had previously created.  It's hard to be certain what went wrong without knowing exactly how the image was created, and exactly how you tried to copy or restore it.

I'm wondering about your statement that you had "**mounted** and partition" the new drive.  How could you mount it before partitioning it?  Or did you simply mean physically **connected**, not mounted.  (Mounting means making the disk part of the active, running file system.)

By the way, I think if you want to use dd to clone an entire disk, both the source and destination disks should be unmounted.

What happens if you just run
```
fdisk /dev/sdd
```

And by the way, you really should consider using another method of cloning you disk.  With dd, a tiny error can destroy your source disk.  There are free programs, such as Clonezilla, that you might find easier and safer.

---

### Post by oldfred on 2013-04-24
Also you really cannot have old drive and new drive connected at the same time. 

They end up with the same UUID, so system is not sure which to use and it may depend on order BIOS mounts drive, using one drive one time and the other another and you really get out of sync.

---

