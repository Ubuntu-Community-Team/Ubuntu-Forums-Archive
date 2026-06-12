---
title: "LVM2 Questions"
date: 2007-06-18
forum: General Help
---

### Post by bpont on 2007-06-18
I'm new to using LVM2 and had some questions:

When I use pvcreate on disks with partitions and data already on them, what happens to the partitions and data?  Is it destroyed / overwritten?

Similarly, if I use vgextend to add /dev/foo, which is already a partition with data on it...what happens to it?

Basically, what I'm trying to do is combine two partitions into one logical volume, which I can mount on /home

I ran pvcreate on /dev/sdb3 (which was then an empty ext3 partition), then I ran vgcreate on same partition.  Then I ran lvcreate, making a partition which basically used up the full capacity of the vg, lastly I wrote the ext3 filesystem to it because for some reason I could not write xfs on it (see: [http://ubuntuforums.org/showthread.php?p=2865720](http://ubuntuforums.org/showthread.php?p=2865720)).

So now I have a working lv at /dev/foo/foo which is mounted at /home.

But I also have another partition on /dev/sdb4, which has lots of data on it and a different (reiserfs) file system.  I would like to run pvcreate on /dev/sdb4, then vgextend to add it same vg as /dev/sdb3, then add /dev/sdb4 to the same logical volume as /dev/sdb3 is on, so all the combined data will be on /home

Can it be done?

---

