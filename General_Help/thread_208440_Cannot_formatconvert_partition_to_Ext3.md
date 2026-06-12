---
title: "Cannot format/convert partition to Ext3"
date: 2006-07-03
forum: General Help
---

### Post by squeky on 2006-07-03
Hi, I'm having a problem converting/formatting a partition to Ext3.  Tried the search with no luck.

Here's my prob--I created 2 partitions a couple weeks ago (formatted both as FAT32 to share with my XP install).  They worked perfect in XP and Ubuntu.  I realized my auto backup of my /home directory was over 4 GB, so I got the data off it and converted it to Ext3 in XP with Partition Magic (was that not smart?).    After the format, it still shows up fine in XP.  So, I restart in 6.06 and use the gnome disks manager.  It still shows up as "Windows Virtual FAT (vfat)".  So, I try again to format as Ext3 in 6.06--it takes a minute then shows Ext3, but it's disabled.  Clicking enable doesn't enable it, so I mount it manually.  The command executes without errors, but the /media/Shared2 folder now points to Lost and Found.  Using the disk manager again, the partition is back to vfat and enabled/accessable.  Tried this twice and triple checked to make sure I'm mounting the right partition.  Here is the mount command I'm using:

```
sudo mount /dev/hdb9 /media/Shared2
```
(where /dev/hdb9 is the device that the disk manager reports).

Can anyone shed any light on this problem?  Thanks!

(after re-reading, I hope that's not confusing)

Brad

---

### Post by DirtDart on 2006-07-03
As you are attempting to format the drive, I would recommend deleting the partition, then re-creating it as an ext3 partition.

> sudo mount /dev/hdb9 /media/Shared2

What do you get when you type this in?  and what is the output of the 'mount' command?

---

### Post by squeky on 2006-07-03
Thanks for the guidance.  I deleted and reformatted (and installed gparted--I was using the disk manager before) and it worked.  Had to set the permissions with chown.  The original output didn't show anything at all.  Great forum, I need to start posting more :)  Thanks again.

---

