---
title: "unable to read superblock"
date: 2014-09-09
forum: General Help
---

### Post by kyle27 on 2014-09-09
The motherboard on my Ubuntu server recently died and I'm in the process of trying to recover the data.

It's probably irrelevant, but since I have no other machine with which to do this, I'm running a virtual Ubuntu server on my Mac in order to mount the hard drive connected via a USB to SATA adapter. I was able to mount and recover the data from my secondary hard drive. However, the primary hard drive is giving me an error.

For some reason hard drive appears to have 2 partitions, although I don't remember partitioning this hard drive (guess that's normal for the primary hard drive?). In any case, the first partition on it just has system files. When I try to mount the second partition is where I run into problems. It says "unable to read superblock" and even looks like part of the hard drive is FAT-fs?? I've attached a screenshot of the error below:
[ATTACH=CONFIG]256316[/ATTACH]

---

### Post by dragonfly41 on 2014-09-10
A couple of links which should help ..

[HOWTO: Repair a broken Ext4 Superblock in Ubuntu « Linux Expresso]("http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/")

[filesystems - Recovering ext4 superblocks - Unix and Linux]("http://unix.stackexchange.com/questions/33284/recovering-ext4-superblocks")

.. and/or run testdisk to help with superblock repair.

---

