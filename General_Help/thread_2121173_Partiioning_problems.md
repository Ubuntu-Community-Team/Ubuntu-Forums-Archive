---
title: "Partiioning problems"
date: 2013-03-01
forum: General Help
---

### Post by thorbs on 2013-03-01
I have had little trouble which have made me end up with three "partitions". The first is just unalocated space. Second is the partition I use, and third is old partition. Now I just want to integrate them all in the partition I use. I have been trying to figure out how to use geparted to do it with out succes. 

How do i get it all settled in one partition?


t.

---

### Post by wojox on 2013-03-01
Are you booting off a Live CD or USB and mounting the disk?

---

### Post by dabl on 2013-03-01
> **thorbs said:**
> 
How do i get it all settled in one partition?



Converting it to a single partition is easy, but then you'll have to fix your system to boot it, because it is presently configured to boot the **second** partition, and if you delete the existing first partition, then your system will be on the new **first** partition.  The GParted menus are a right-click while the cursor is on the target partition.

May I suggest you shrink the existing first partition to 1GB, and change the filesystem to swap.  That way your system will remain on the second partition.  You can delete the existing third partition, and then expand the second partition to use all of the unallocated space.

Note -- this type of change can take a very long time -- prepare to go do something else for some hours.

Also note -- if your /etc/fstab mount lines use UUIDs, then these may change after the re-partitioning work.  If that happens, you can use this command to see the new configuration and UUIDs:

```
sudo blkid -c /dev/null -o list
```

This will show you what you need to edit /etc/fstab and paste in the correct UUIDs.

---

