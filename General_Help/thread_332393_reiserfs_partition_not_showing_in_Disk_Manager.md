---
title: "reiserfs partition not showing in Disk Manager"
date: 2007-01-06
forum: General Help
---

### Post by jrs3512 on 2007-01-06
I have two HDD in my machine.  On one, ext3, I have the OS and swap, the other is for photos, videos, etc.  It was working fine untill about two weeks ago, when Disk Manager started showing the filesystem as "Unknown" as opposed to reiserfs.  

GParted still shows it as reiserfs, but it tells me "Unable to read the contents of this filesystem! Because of this some operations may be unavailable.  Did you install the correct plugin for this filesystem?"

I am in desperate need of geeting these photos off this drive and backed up, please advise.

JRS

---

### Post by tomchuk on 2007-01-06
Ugh, I've lost way too much data to Reiser over the years. Try the following in this order, attempting to mount the filesystem in between each:
```

sudo fsck.reiserfs --check /dev/hdXn
sudo mount -r -t reiserfs /dev/hdXn /mnt/whatever
sudo fsck.reiserfs --fix-fixable /dev/hdXn
sudo mount -r -t reiserfs /dev/hdXn /mnt/whatever
sudo fsck.reiserfs --rebuild-sb /dev/hdXn
sudo mount -r -t reiserfs /dev/hdXn /mnt/whatever
sudo fsck.reiserfs --rebuild-tree /dev/hdXn
sudo mount -r -t reiserfs /dev/hdXn /mnt/whatever

```

---

### Post by jrs3512 on 2007-01-06
After each attempt to run fsck I got the following error:
[INDENT]The problem has occurred looks like a hardware problem. If you have bad blocks, we dvise you to get a new hard drive, because once you get one bad block  that the disk drive internals  cannot hide from your sight,the chances of getting more are generally said to become much higher  (precise statistics are unknown to us), and  this disk drive is probably not expensive enough  for you to you to risk your time and  data on it.  If you don't want to follow that follow that advice then  if you have just a few bad blocks,  try writing to the bad blocks  and see if the drive remaps  the bad blocks (that means it takes a block  it has  in reserve  and allocates  it for use for of that block number).  If it cannot remap the block,  use badblock option (-B) with  reiserfs utils to handle this block correctly.

bread: Cannot read the block (8210): (Input/output error).

Aborted[/INDENT]
And after each attempt to mount the partition I got the following error:
[INDENT]
mount: wrong fs type, bad option, bad superblock on /dev/hdb2, missing codepage or other error In some cases useful info is found in syslog - try dmesg | tail  or so[/INDENT]

I am not sure how to use dd or dd_rescue that well, any sugestions would be very appreciated, thanks

---

