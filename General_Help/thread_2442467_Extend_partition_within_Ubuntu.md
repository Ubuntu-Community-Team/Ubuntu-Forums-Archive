---
title: "Extend partition within Ubuntu"
date: 2020-05-04
forum: General Help
---

### Post by cAlpha on 2020-05-04
I have a Windows-based dual boot system with the original Win 7 OS, Ubuntu 18.04 on a separate partition and a shared NTFS partition for files, etc. 

I originally carved out 40 GB for the Ubuntu partition, but am getting close to filling it after a number of months and would like to extend its space.

It doesn't seem possible to extend it natively within gparted (via right-click, min and max-size are the same and both equal to the current space allocation), and I also can't extend the shared partition and then resize it to move space adjacent to the Ubuntu partition.

I carved out additional space from the Win7 partition while in Windows, but don't seem able to use this to extend my Ubuntu partition.  I've included a snip of my existing partition layout below.  Any guidance is appreciated. 

[ATTACH=CONFIG]285736[/ATTACH]

---

### Post by CatKiller on 2020-05-04
You can't change a partition that's currently mounted, and you can't unmount a partition that you're trying to run gparted from - see the key symbols that show the partitions are locked?

You also haven't got the unallocated space next to the partition you want to extend into it, yet. You'd need to shunt your NTFS data partition along first. It's probably best to do that part in Windows, too, since it's a Windows-native filesystem.

Once you've done that you can boot from a live image (so that you can run gparted from somewhere other than the partition you're fiddling with) and do your resizing.

---

### Post by HermanAB on 2020-05-04
Hmm, I am allergic to changing partitions, since that is a very good way to lose all your data...

My preferred solution is to make a new partition, call it something like /data, create a proper file system on it and put a link to it from somewhere more convenient if necessary.

---

### Post by ActionParsnip on 2020-05-04
Make a backup of your important data before any of this

---

### Post by TheFu on 2020-05-04
Without LVM, there are huge risks with merging storage because the partitions must be physically next to each other.  Changing partitions can change the UUID and definitely will change the device "file" so be ready to fix the fstab.

If the ubuntu install used LVM, then you can create a partition in the empty space, create a PV there, then extend the existing VG there and finally, use lvextend for the existing LVs.  All of this could be done while the OS is online.  LVM has some complexity, but also great flexibility.

If all 40gb are on a single partition today, you can do some clean-up using the unused storage.  Unix is dumb.  Very few areas have to be in specific places on the HDD cylinders. Everything else just needs to be in the right directory with the right permissions.  That  means we can move /home/ from the 40G storage into the new storage area, if we like.  it just needs a partition, a file system, the files moved over, then the new storage mounted to the correct place.  as long as the mount makes the directories and files in the right place, fine.  

I like a layout like this: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)  
25G for /
4.1G for swap
Other places sized as needed.  I don't keep any media in HOME.

---

### Post by cAlpha on 2020-05-05
> **TheFu said:**
> Without LVM, there are huge risks with merging storage because the partitions must be physically next to each other.  Changing partitions can change the UUID and definitely will change the device "file" so be ready to fix the fstab.

If the ubuntu install used LVM, then you can create a partition in the empty space, create a PV there, then extend the existing VG there and finally, use lvextend for the existing LVs.  All of this could be done while the OS is online.  LVM has some complexity, but also great flexibility.

If all 40gb are on a single partition today, you can do some clean-up using the unused storage.  Unix is dumb.  Very few areas have to be in specific places on the HDD cylinders. Everything else just needs to be in the right directory with the right permissions.  That  means we can move /home/ from the 40G storage into the new storage area, if we like.  it just needs a partition, a file system, the files moved over, then the new storage mounted to the correct place.  as long as the mount makes the directories and files in the right place, fine.  

I like a layout like this: [https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277)  
25G for /
4.1G for swap
Other places sized as needed.  I don't keep any media in HOME.

So, is that to say I could conceivably move my existing Ubuntu partition to the unallocated partition I created?  

I have a second external HD onto which I can temporarily move the Share partition contents.  Assuming I'd *really* like to not mess up my existing Ubuntu partition (ie, I'd be willing to deal with the intermittent pop-ups saying I only have 1.1GB of space left versus having to start from scratch), am I correct in assuming my best course is a version of the following:
(1)  Back-up Share partition and fstab;
(2)  Wipe Share partition and combine with existing open space to create a single open partition adjacent to both Windows and Ubuntu;
(3)  Try to extend Ubuntu partition into this from within Windows (or Ubuntu if it works);
(4)  Create new Share partition from remaining space; modify fstab with new UUIDs, etc. per new layout for mount points as part of startup

---

