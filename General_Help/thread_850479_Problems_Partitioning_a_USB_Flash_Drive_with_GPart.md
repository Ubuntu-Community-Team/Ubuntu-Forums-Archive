---
title: "Problems Partitioning a USB Flash Drive with GParted"
date: 2008-07-05
forum: General Help
---

### Post by xenolalia on 2008-07-05
Hi!  I've been trying for some time to make a live Ubuntu flash drive -- ultimately, I want two partitions: #1 FAT32 5.8 GB, #2 FAT32 2.0 GB.  For some reason, whenever I create the second partition, it always comes out as filesystem "unknown" (in gparted).  When I go to try and mount the second partition (sdi2), I get this:

mount: wrong fs type, bad option, bad superblock on /dev/sdg2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Although gparted sees sdi2 as filesystem type "unknown," fdisk sees sdi2 as FAT32.  Since, for my purposes, it doesn't really matter what type of filesystem sdi2 is, I've tried formatting it as ext2, ext3, fat16, and others, none of which have worked.  When I tried formatting sdi2 as ext2/ext3, gparted did this . . . strange . . . fixing . . . superblock . . . thing :wink: -- by the way, I'm a complete novice.  Needless to say, it didn't work.  I've attached the gparted log file -- I can't make any sense of it, but the last line does say something about a . . . a magic number (?)  I don't know.  Help would be appreciated.  I'm getting kind of desperate.

Thanks in advance!

---

### Post by kuja on 2008-07-05
Why the Fat32 partition? AFAIK Windows can't handle removable devices with multiple partitions, so you might as well use a more modern filesystem (e.g.: ext3), if you still plan on keeping a seperate storage partition after hearing that.

I've really no idea what to do aobut the "bad superblock" bit though. The only idea I've got is to run something like ```
sudo dd if=/dev/zero of=/dev/sdg bs=2048
``` Which will overwrite the device from beginning to end with zero's. [color=red](WARNING: Not reversible! Will overwrite **everything** on the drive.)[/color]

Afterwards, I would repartition and try things over again.

---

### Post by xenolalia on 2008-07-06
Thanks for the speedy reply!

My understanding was that Windows can only see the first partition on a removable drive, so I figured that I would make the first partition my storage partition.  

And, if I understand correctly, doing

sudo dd if=/dev/zero of=/dev/sdg bs=2048
would be like starting from scratch . . . superblocks and all.  Right?

Thanks again!

(Oh, and after I received your reply, I realized that I'd forgotten to attach the gparted log :).  Sorry 'bout that)

---

### Post by kuja on 2008-07-06
I've tried partitioning a flash drive in a similar way before and windows wouldn't recognize it when I plugged it in ...... what I see on google seems to agree with me.

Anyhow, yes, that command will overwrite every bit on that drive with 0s - in other words, yes, superblock's and all.

---

