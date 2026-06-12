---
title: "Need Help Recovering Data from Accidental Ubuntu 12.10 Install on Ext 4 Partition"
date: 2013-04-26
forum: General Help
---

### Post by cyf on 2013-04-26
I mistakenly installed 12.10 Desktop on my 3TB data drive I specified , and upon realizing it, I tried to recover data by looking for the old partition map--which of course was not there.  However, I read about backup superblocks in this article:

[http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/](http://www.cyberciti.biz/faq/linux-find-alternative-superblocks/)

and this is the result:

```
xbmc@Uhh:~$ sudo dumpe2fs /dev/sdd1 | grep -i superblock
[sudo] password for xbmc: 
dumpe2fs 1.42.5 (29-Jul-2012)
  Primary superblock at 0, Group descriptors at 1-175
  Backup superblock at 32768, Group descriptors at 32769-32943
  Backup superblock at 98304, Group descriptors at 98305-98479
  Backup superblock at 163840, Group descriptors at 163841-164015
  Backup superblock at 229376, Group descriptors at 229377-229551
  Backup superblock at 294912, Group descriptors at 294913-295087
  Backup superblock at 819200, Group descriptors at 819201-819375
  Backup superblock at 884736, Group descriptors at 884737-884911
  Backup superblock at 1605632, Group descriptors at 1605633-1605807
  Backup superblock at 2654208, Group descriptors at 2654209-2654383
  Backup superblock at 4096000, Group descriptors at 4096001-4096175
  Backup superblock at 7962624, Group descriptors at 7962625-7962799
  Backup superblock at 11239424, Group descriptors at 11239425-11239599
  Backup superblock at 20480000, Group descriptors at 20480001-20480175
  Backup superblock at 23887872, Group descriptors at 23887873-23888047
  Backup superblock at 71663616, Group descriptors at 71663617-71663791
  Backup superblock at 78675968, Group descriptors at 78675969-78676143
  Backup superblock at 102400000, Group descriptors at 102400001-102400175
  Backup superblock at 214990848, Group descriptors at 214990849-214991023
  Backup superblock at 512000000, Group descriptors at 512000001-512000175
  Backup superblock at 550731776, Group descriptors at 550731777-550731951
  Backup superblock at 644972544, Group descriptors at 644972545-644972719



```

I then ran: 

```
sudo e2fsck -f -y -b 550731776 /dev/sdd1 -C 0

```

and a few hours and a bunch of duplicated clones later, including some wrong directory counts later:

```
Directories count wrong for group #21120 (0, counted=1).
Fix? yes


Free inodes count wrong for group #21696 (8192, counted=8172).
Fix? yes


Directories count wrong for group #21696 (0, counted=10).
Fix? yes


Free inodes count wrong for group #22240 (8192, counted=8187).
Fix? yes


Directories count wrong for group #22240 (0, counted=4).
Fix? yes


Free inodes count wrong (183148533, counted=182471447).
Fix? yes



```
(there were many, many screens of this)

the computer spit out:

```
/dev/sdd1: ***** FILE SYSTEM WAS MODIFIED *****
/dev/sdd1: 677097/183148544 files (2.3% non-contiguous), 655823355/732566272 blocks



```

However, when I tried to mount the file system using:
 
```
xbmc@Uhh:~$ sudo mount -o sb=550731776 /dev/sdd1 /mnt/rescue

```

I got the dreaded:

```
mount: wrong fs type, bad option, bad superblock on /dev/sdd1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```
with the dmesg being:

[142724.935882] EXT4-fs (sdd1): VFS: Can't find ext4 filesystem

Searched and all I found were similar problems, but no real solutions.

I know at least some of the original files before the install are still on the disk because they were listed during the time the e2fsck was running--albeit with a directory like /???/Pictures/Birthday ("/???" is the actual directory that was shown before the Picture directory--one of the directories that I had).

I'm trying to recover the structure data as much as the files themselves.  I have a backup of most of the drive, but I hadn't ran a recent back-up (yeah, yeah, I know).  I've looked everywhere, and I'm stumped...

This is the last time I leave "non-essential" drives plugged in during an install.  I promise!

---

### Post by cyf on 2013-04-27
Nothing?

---

