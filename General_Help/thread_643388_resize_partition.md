---
title: "resize partition"
date: 2007-12-17
forum: General Help
---

### Post by aaronmeade on 2007-12-17
I apologize in advance if this seems like a duplicate thread.   The other  threads on this topic are old, and I don't know if anyone is reading them any longer.

So I've installed Ubuntu on an extended partion.  After getting the kinks worked out (3dgfx driver, widescreen resolution, etc.) and backing up data I am ready to get rid of my windows partion all together.   

1) I deleted the Windows partition so that in now appears as unallocated in Gnome Partition Editor.

2) I booted with LiveCD and attempted to umount the Linux partition to resize it.  I could not do this from the command line because my partion was not found, although it appears in Partition Editor.

3) Partition Editor will allow me to unmount the partition, but when I try to resize it will not let me use the unallocated space, which is the whole point.

Any ideas?  I am rather new to partitioning, so I may be missing something fundamental.

Thanks for your help.

attached: screenshot of my partitions in gparted.

---

### Post by ajmorris on 2007-12-17
hi there,
As you are using a reiserfs partition, to be able to resize your partition to fill the un-used space, the un-used space must be after the reiserfs partition, and inside the extended partition also, so, resize the extended partition to fill the space, then the unallocated space will be inside the extended partition, move this unallocated space to after the reiserfs partition, then expand the reiserfs partition into it.

---

### Post by divague on 2007-12-17
i did that same thing on my friend's computer he wanted windows out so i downloaded the gparted livecd and i used it to resize the partition
[http://gparted-livecd.tuxfamily.org/](http://gparted-livecd.tuxfamily.org/)

---

### Post by CouchMaster on 2007-12-17
You could just reformat it and use it as storage.

---

