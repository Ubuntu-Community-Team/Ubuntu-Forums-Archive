---
title: "fsck fails on Ext3 journal superblock has an unknown read-only flag"
date: 2007-04-25
forum: General Help
---

### Post by julv on 2007-04-25
Hello,

2 days ago, my edgy boot failed as my /home partition (hdf2, ext3) couldn't be mounted due to a fsck failure.

I booted with the live cd, and launched gparted, which  seemed to read the partition structure ok on the associated hdd.
Then, i tried to check the partitions with fsck, but it failed quickly on both the partition of the drive, with slightly different messages.
 - on the first partition of the drive (hdf1 ext3), the failure was due to a bad superblock.
After some research, i started testdisk, and got the alternate superblocks for both partition, and i could fix hdf1 using one of them (seems ok now, i can mount it, and browse, but i didn't really check every file...)
- However, this method didn''t work with hdf2, i keep having the same message, whichever the superblock location (although if i pick a random number for the location, i get a "bad superblock" message):

> ubuntu@ubuntu:~$ sudo e2fsck -b 98304 /dev/hdb2
e2fsck 1.40-WIP (14-Nov-2006)
Ext3 journal superblock has an unknown read-only feature flag set.
Abort<y>? yes

I couldn't really find anything usefull on that one... except maybe reformatting the partition, but i'm not ready to give up yet, so i'm open to any ideas ! I was thinking maybe to reformat it to ext2 without changing anything, thus getting rid of the journaling problem, but i'm not sure this would leave my data intact. opinion ?

---

