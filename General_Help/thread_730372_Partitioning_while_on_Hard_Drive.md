---
title: "Partitioning while on Hard Drive"
date: 2008-03-20
forum: General Help
---

### Post by GearedForWar on 2008-03-20
Is there anyway I can use the partition editor and edit my hard drive while I'm on it?  I would like to shrink my Windows Partition for room for 8.04.  It is not giving me the choice to do it.  Can I not do it because I am using the hard drive?  I am using GParted.

---

### Post by Joe Dinmore on 2008-03-20
I believe not.
Best you boot from the Live CD and re-partition that way

---

### Post by GearedForWar on 2008-03-20
Thanks.  Only asking because my Live CD for 8.02 Dev is being a bitch.  TY.:)

---

### Post by louieb on 2008-03-20
Right click on it and select unmount. That should remove the lock and let you shrink it. The only partitions you can't unmount are the ones that hold  parts of the Ubuntu install.

---

### Post by forrestcupp on 2008-03-20
Download and use [GParted LiveCD](http://gparted-livecd.tuxfamily.org/).  That will do the trick for you.  If you have trouble booting to the desktop, choose the option to force vesa.

---

### Post by bodhi.zazen on 2008-03-20
> **GearedForWar said:**
> Is there anyway I can use the partition editor and edit my hard drive while I'm on it?  I would like to shrink my Windows Partition for room for 8.04.  It is not giving me the choice to do it.  Can I not do it because I am using the hard drive?  I am using GParted.

You are best off partitioning from a live CD. The ubuntu desktop CD will do.

If you like, you can resize any partition from the hard drive EXCEPT the one you are running Ubuntu from.

If you can not resize your windows partition it is either mounted or needs to be defragmented.

If you are running Vista, however, you should use the tools in Vista to resize your windows partition.

---

### Post by GearedForWar on 2008-03-20
I think it was becuase they are unmounted.  I just wasted one of my CD's for the 7.10 live CD thinking that my 8.10 CD was slow.  They both got errors so I figured that they needed to me unmounted from what louieb said.  And what is mounting and unmounting?

---

### Post by bodhi.zazen on 2008-03-20
mounting is the process where you prepare the file system for use.

[http://www.tuxfiles.org/linuxhelp/mounting.html](http://www.tuxfiles.org/linuxhelp/mounting.html)

You can un-mount them from gparted. Right click on the partition and select unmount.

---

### Post by GearedForWar on 2008-03-20
ok it scared the crap out of me...First when I unmounted it, the mount point dissappeared of course, but then it doesn't know how big the partition is and how much is used up.  Just ---.

Did it remove everything off that partition?

---

### Post by forrestcupp on 2008-03-21
> **bodhi.zazen said:**
> You are best off partitioning from a live CD. The ubuntu desktop CD will do.

If you like, you can resize any partition from the hard drive EXCEPT the one you are running Ubuntu from.

If you can not resize your windows partition it is either mounted or needs to be defragmented.

If you are running Vista, however, you should use the tools in Vista to resize your windows partition.

Personally, I think GParted LiveCD is much easier to use.  It's made specifically for this and nothing else.  When you boot it up, it's just ready to go for that specific purpose.  Also, there is no need to unmount anything because its whole point is messing with partitions so it doesn't ever mount any of them.  And to top it all off, if you don't have an Ubuntu CD, this one is a much smaller download.

About Vista, its resizing capabilities are very limited and it doesn't do things that you think it should sometimes.  It especially doesn't work well if you have ext3 partitions.  I tried it once and it didn't do what I needed it to do.

---

### Post by GearedForWar on 2008-03-21
I'm trying the Live CD for GParted.  I'm getting a can't read file system for the windows(NTFS) partition and I heard the Live CD can fix that so I'm trying it out.

---

### Post by GearedForWar on 2008-03-21
Ok now nothing is working.  Everytime I use a partition editor it fails.  PartitionMagic, Gparted, Fdisk.


The Live CD's don't do anything either.

All fail to shrink my C:\ partition.


Anyone have an idea?

---

