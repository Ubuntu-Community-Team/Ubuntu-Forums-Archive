---
title: "Using gparted to resize the left of a partition"
date: 2007-01-26
forum: General Help
---

### Post by CSMatt on 2007-01-26
I have found that gparted only will resize partitions of there is empty space to the right of the partition, not the left.  Now, I intend to resize my NTFS partition (which is in front of my Ext3 partition) in order to give more room for my Ext3 partition.  I can't, however, seem to be able to resize the Ext3 partition so that it will use the now empty space between it and my NTFS partition.  How do I do this?

---

### Post by meng on 2007-01-26
Try the new GParted Live CD (version 0.3.3 or higher), it has improved support for resizing and moving partitions of various types.

---

