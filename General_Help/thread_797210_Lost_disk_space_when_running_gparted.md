---
title: "Lost disk space when running gparted"
date: 2008-05-17
forum: General Help
---

### Post by Aramaz on 2008-05-17
Hi, I'm pretty new to ubuntu, but I like it alot.

Today I tried shrinking my ubuntu partition using gparted but I think I might have aborted it or something. I was checking the detailed log where it says what gparted is doing. It was at a point where it was expanding the filesystem or something, it said: "nothing to do!". I got distracted at this point and thought it was finished and clicked the close button. (Didn't get any warning messages... I'm not sure now if it was finished or not)

Anyways, when I rebooted the only thing that had happened was that the used space of the partition I was shrinking had gone up by 25 gig (the space I was shrinking with), and there is no new partition... Is there some way I can reclaim this space (maybe it's in a temporary file somewhere created by gparted?), or do I have to redo my installation to get it back?

I have googled a while for answers, but have not found any...

Thanx for your help!

---

### Post by storm99999 on 2008-05-17
There's this really nifty program in [Applications] [Accessories] [Disk Usage Analyzer].  Clicking on "Scan Filesystem" should help tell you where the file is, as that would be a large chunk of the visual circle graph.

---

### Post by fyo on 2008-05-17
> **Aramaz said:**
> Anyways, when I rebooted the only thing that had happened was that the used space of the partition I was shrinking had gone up by 25 gig (the space I was shrinking with), and there is no new partition... Is there some way I can reclaim this space (maybe it's in a temporary file somewhere created by gparted?), or do I have to redo my installation to get it back?

There's a good thread here: [http://ubuntuforums.org/showthread.php?t=795066](http://ubuntuforums.org/showthread.php?t=795066)

A likely culprit would seem to be that gparted resized the filesystem ahead of resizing the partition. You can run the following command (from a terminal) to reclaim any such space (assuming you are using ext2 or 3):

```
resize2fs /dev/XXX
```

Where you should replace XXX with the relevant partition (use "df" from a terminal to get a list of mounted partitions - gparted will also give you the information). Running resize2fs without any options, like above, will simply resize the filesystem to take up the maximum amount of space possible on the partition.

---

### Post by Aramaz on 2008-05-17
fyo> many thanx, that solved the problem! :)

storm99999> thanx for the tip, I was looking for such a program (fsv), I'm sure I will use it many times in the future! :)

---

### Post by fyo on 2008-05-17
Please mark the thread as "solved" (option available under "thread tools").

---

