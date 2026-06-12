---
title: "Partitioning to use all available space on HD"
date: 2007-07-30
forum: General Help
---

### Post by Rudy507 on 2007-07-30
Hey guys,
I've got a 30 GB hard drive running on an old Dell Inspiron i've had for a couple years. Off an on, I've been a very amateur linux user, and as of now, I still don't know how to do much. 

I'm running a dual boot of Win XP and Fiesty Fawn right now. I use Windows mostly (partly because I've never been able to get my integrated broadcom bcm43xx card to work, despite how often I google or try fixes I find here or elsewhere on the net, and despite how many 'linux gurus' look at my computer). All of that to say, I want to learn, and use it as my primary os. 

Sorry for the rant.. back on subject....

I'm trying to figure out how to use all 30 Gb of disk space. According to fdisk, here's my current setup: 
```
Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/sda2            1021        2064     8385930    f  W95 Ext'd (LBA)
/dev/sda3            2065        3565    12056782+  83  Linux
/dev/sda4            3566        3648      666697+  82  Linux swap / Solaris
/dev/sda5            1021        2039     8185086    7  HPFS/NTFS

``` 

According to Gpart, I have an almost 28 GB harddrive. Due to a couple recent repartitioning changes I've made, I have an empty 196Mb sitting in the middle of my harddrive right now doing nothing.

I want to merge that onto my NTFS Extended partition. 

I also want to figure out if I can ever get Gpart to tell me I have a 30Gb drive, and try to merge those extra 2 Gigs onto wherever I can put it.

My question is this: 
/dev/sda5 is a valid Windows partition that I need to keep. Based on what I've read about the lable "W95 Ext'd (LBA)", I'm going to assume that /dev/sda2 is the empty 196Mb I have.... am I correct?

If so, is there a way to merge it onto /dev/sda5?

Also, do you think there's an extra 2 gigs sitting around somewhere that's probably intended to be used for dell manufacturer stuff and hidden, that I can access and use?

Thanks for any help,
David

---

### Post by aquavitae on 2007-07-30
> /dev/sda5 is a valid Windows partition that I need to keep. Based on what I've read about the lable "W95 Ext'd (LBA)", I'm going to assume that /dev/sda2 is the empty 196Mb I have.... am I correct?
/dev/sda isn't really a usable partition, its and extended partition.  This is because the partition table of a hard drive can only contain four entries.  To get around this, you use extended partitions (which are in the partition table) containing logical partitions which are just like normal partitions, except that there table is inside the extended partition.  On your drive, /dev/sda is an extended partition containing /dev/sda5.  However, but looking at the block size, you can see that /dev/sda5 is smaller than /dev/sda2 and so there is some unallocated space at the end of /dev/sda5.  
> If so, is there a way to merge it onto /dev/sda5?
You should be able to add it to /dev/sda5 by simply resizing /dev/sda5 using gpart, fdisk, or whatever your preferred partitioner is.  Just a note of warning - I'm not sure what the support is like in linux for resizing ntfs partitions.  I'd advise a bit of googling before you do it just to check that its ok.  Otherwise you might be able to do it through windows somewhow.
> Also, do you think there's an extra 2 gigs sitting around somewhere that's probably intended to be used for dell manufacturer stuff and hidden, that I can access and use?I think its more likely that its just a perculiarity of gpart.  I know different systems sometimes report different sizes for the same drive.  I have a 200G hd which windows reports as 196G, windows fdisk reports it as 192G, linux fdisk says 198G, and as far as I remember parted says its 203G.  

Anyway, aside form that, if you look at your partition table, you'll see that your disk has 3648 cylinders.  Also, that last primary partition (/dev/sda4) starts at 3566 (cylinders) and ends at 3648, i.e. the last cylinder.  There are also no gaps between any of the partitions (i.e. end of /dev/sda1 = start of /dev/sda2+1) so apart from the space after /dev/sda5 its all allocated.

I hope you managed to make sense of my explanations - you might want to google (or wikipedia) partition tables to learn more.

---

### Post by indytim on 2007-07-30
One additional caution with respect to re-sizing NTFS partitions with GParted (or GParted Live).  Do ONLY one operation at a time.  Do not try to run multiple operations with a single submittal.  

I made that painful mistake about a year ago.  Ended up hosing my partition table.  Due to inadequate backups at the time, had to re-build my whole system from scratch (4 ops).

IndyTim

---

### Post by Rudy507 on 2007-07-30
This all makes sense. Thanks guys.

---

