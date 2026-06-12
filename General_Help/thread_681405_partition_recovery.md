---
title: "partition recovery"
date: 2008-01-28
forum: General Help
---

### Post by agrajagzz9 on 2008-01-28
Hi

Recently I wanted to erase some of my hard drives using [Darik's Boot and Nuke]("http://dban.sourceforge.net/"). I backed up all of my stuff to my largest hard drive, then disabled it and started up DBAN. Unfortunately, I accidentally disabled the wrong drive and DBAN started erasing part of my backup drive.
Luckily I realised this a few seconds after it started, so i hit the power button and I think most of my files are ok. However, some of the partition table seems to have been overwritten. I have been able to recover the partition table (a single ext3 partition over the whole drive) using TestDisk. However, attempting to mount the partition returns the following error, indicating filesystem damage:
```
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```
Using the superblock tool in Test disk returns the following for that partition:
```
  Linux                    0   1  1 60800 254 61  976768000 [videos]
superblock 32768, blocksize=4096
superblock 98304, blocksize=4096
superblock 163840, blocksize=4096
superblock 229376, blocksize=4096
superblock 294912, blocksize=4096
superblock 819200, blocksize=4096
superblock 884736, blocksize=4096
superblock 1605632, blocksize=4096
superblock 2654208, blocksize=4096
```

I don't know much about how filesystems work, but i think that means that the first superblock is damaged.

Is it possible to recover the filesystem, and how?

thanks for your help.

---

### Post by agrajagzz9 on 2008-01-29
I ran fsck on the partition and all my stuff is there!! :D

---

