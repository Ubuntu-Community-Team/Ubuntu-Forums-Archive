---
title: "Boot Sector Error"
date: 2007-04-26
forum: General Help
---

### Post by charleseddy on 2007-04-26
:confused: I have not yet found a solution to this.  When I start Ubuntu it comes to a maintenance shell due to a fsck error and it's writing the output to the file /var/log/fsck/checkfs.  The following is the output of the file.  Any ideas?  I think this may be related to my computer now freezing randomly.
__

Log of fsck -C -R -A -a 
Thu Apr 26 03:04:06 2007

fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
There are differences between boot sector and its backup.
Differences: (offset:original/backup)
  65:01/00
  Not automatically fixing this.
/dev/hda2: 20699 files, 972628/1599581 clusters
/dev/hda5 is mounted.  e2fsck: Cannot continue, aborting.


fsck died with exit status 8

Thu Apr 26 03:04:20 2007
----------------
__

---

