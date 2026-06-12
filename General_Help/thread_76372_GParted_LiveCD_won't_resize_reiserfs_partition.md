---
title: "GParted LiveCD won't resize reiserfs partition"
date: 2005-10-15
forum: General Help
---

### Post by Rounan on 2005-10-15
Hello,

I'm trying to install Breezy, and am trying to re-tool a single-partition Warty install to a /home and two seperate / partitions - one Warty, one Breezy.

So, I downloaded the Breezy install and livecds, and tried to re-partition from the livecd environment. Gparted won't resize the partition. It's 40GB with ~5GB used, and I'm trying to resize it to 10GB. Gparted throws up a "resizing" dialogue, during which part the partition graph reflects the change. After that's done, it starts "scanning all devices". Once it re-scans the partition table, the change reverses - or, no change was actually made.
Interestingly enough, though, it can add partitions - originally I queued up all the operations I wanted: resize, create extended partition with 2 logical partitions inside. Operation 1 failed, 2 succeded, and 3 and 4 failed - I now have a 0 byte extended partition sitting on the end of my drive.

The installed system is unaffected - if the reiserfs filesystem was ever resized, it was undone because my / partition is still 40GB.

I also tried this with the Warty livecd, and I get the same results. It's interesting to note, however, that scanning drives takes less than a second on Warty, and close to a minute on Breezy - pretty serious regression just to read a partition table.

I've read posts that libparted is having troubled with the /dev/mapper system used by the liveCD. Is there a fix for this? Has anyone else experienced similar problems?

I'm running Breezy AMD64, haven't run an i386 livecd to rule out that as the cause. I wouldn't accept "use 32-bit" as a solution in any case. The hardware:
MSI K8N Neo4/SLI mobo
Athlon64 3700+
WD 74GB Raptor drive on SATA

---

### Post by Pausanias on 2005-10-15
You need to unmount the partition and run resize_reiserfs first. Only then can you use a paritition editor to resize the partition.

It's crazy, no? Just be thankful you didn't use plain old parted. It would have trashed your data, like it did mine before I found out about resize_reiserfs.

---

### Post by Rounan on 2005-10-15
Well, I tried the SystemRescueCD with qtparted to do the same thing, and it ended up trashing the partition, so I've since reinstalled fresh. I backed up all data, of course, so no big deal.

Shouldn't tools like gparted be smart enough to call resize_reiserfs first on their own? That's why they exist, after all. I'm pretty sure that's what it was doing, and the resize failed for some reason or other.

---

### Post by Pausanias on 2005-10-16
Not to my knowledge---nothing calls resize_reiserfs. Maybe it's because it has a huge warning on startup that "this is BETA software and use it at your own risk." Well, it seems to work without any hitches.

What all the partitioning programs should do is spit out a warning that says, "Hey, are you sure you've run resize_reiserfs first?" That would be no effort to code and save a lot of people confusion. And lost data.

---

### Post by sjmorgan on 2005-10-23
[http://bugzilla.ubuntu.com/show_bug.cgi?id=18353](http://bugzilla.ubuntu.com/show_bug.cgi?id=18353)

gparted is pretty crappy to be honest. Every time I've attempted to use it it's revealed yet another show stopping bug.

---

