---
title: "Drives locked within Gparted"
date: 2006-11-02
forum: General Help
---

### Post by Roger Mudd on 2006-11-02
I'm hoping to resize the partition on an external USB hard drive so that I can create a second 25GB FAT32 partition on which I can store data to be shared by my XP and Dapper installations (dual boot). The drive currently consists of one large NTFS partition.
I have installed Gparted, but when I go to resize the partition it is locked. In fact, all the partitions on my three hard drives are locked. Any way to unlock these?

---

### Post by sefs on 2006-11-02
Your usb device probably auto mounted which is why you see locks.  I dont think you can resize partitions on a mounted filesystem.

You can either boot with a live CD and do your partition from there or simply go into nautilus first and right click on the USB drive in question and click on the unmount menu item.  Once unmounted you should be good to go with partitioning.

---

### Post by Roger Mudd on 2006-11-02
Thanks for the quick reply sefs. One other question:
If I unmount the drive, Gparted only shows me the total space available (all 250GB) and not total space occupied. Is it safe to repartition this drive if I have data on it that I want to keep? I've heard of people defragmenting until the cows come home in XP before partitioning with Gparted. Is this necessary to ensure that the data is contiguous on the front end of the drive?
Just don't want to lose data on the external as it's my only back-up at the moment.

---

### Post by sefs on 2006-11-02
What to say here....the safe rule of thumb is always have a backup.  What I would do is make a back up and then test it to see if it works.  

I am not sure if Gparted is able to do non-distructive repartitioning if data is scattered about the place, which is probably less of a risk in linux than windows?

Personally although it is probably a tried and tested thing (resizing partitions with data on them) I would never trust it.  I would prefer to backup and recreate partitions as I want them.  I am talking about a data only drive here, where I can just do a quick copy of the files to one place, repartition and copy back.  That way i'm not second guessing or taking risk.

ps in your first post you said "resize" in your second post you said "repartition"  to me those are two diffent things where the first can be possibly non-destructive and the second (deleting old partitions and recreating new ones) is instant data loss?

Hopefully a guru will drop by to add there two pence.

---

