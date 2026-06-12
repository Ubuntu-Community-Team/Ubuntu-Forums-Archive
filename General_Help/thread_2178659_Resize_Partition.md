---
title: "Resize Partition"
date: 2013-10-04
forum: General Help
---

### Post by Satyadeo_Thakur on 2013-10-04
Hello,

I had a dual-boot in my laptop with Windows 8 being installed along with Ubuntu. Today I decided to ditch windows completely and hence removed it using OS-Uninstaller. Now the breakup of the hard-disk looks like this (attached screenshot).

[ATTACH=CONFIG]246754[/ATTACH]

Now I'm trying to merge the all empty/unused space into one partition (named Mass Memory in screenshot). But I'm not able to do it. Also I am not sure about the swap memory partition which I create during installation of ubuntu. Another thing is that the windows partition still shows 'boot' flag. Does it affect Ubuntu partition?

Please guide me.

---

### Post by TheFu on 2013-10-04
That picture doesn't look like a Windows8 dual boot machine. Are you certain this is the right HDD?
For the best help, please run boot-info and post the created link back here ... see my signature for links to that tool.

With mixed file systems, the easiest solution is to backup directories ... something like **fsarchive** can do that for NTFS and EXT2/3/4, jfs, .... partitions. Then you can repartition as you wish and restore everything to whatever file system you like. Changing from NTFS to EXT4 or whatever isn't a big deal provided you are happy losing any permissions/ownership data that NTFS may have had.
**rsync** can be used too - or any of 50 other data backup tools.
BTW, I just went through all this a few days ago.  Migrated 7 partitions from a 160G netbook HDD to a new, AF 500G netbook HDD.  The migration wasn't too efficient - I used dd_rescue to perform a bit-for-bit copy at the device level (that includes partitions) and discovered that partition alignments had to be fixed afterwards thanks to the 512B --> 4KB sector alignment changes.  Used a system rescue flash boot to solve the issues.  Took about 4 hrs to do the initial copy (USB2 sucks), then another 4 hrs to backup the file systems, move the empty partitions for better alignment, then restore the data again.  I'm running on that netbook now.

Be certain to use **parted** and **gparted** to automatically handle the alignment issues. Many versions of other tools do not do this automatically.

However, the boot-info data would be a big help.

---

### Post by Mark Phelps on 2013-10-05
To "merge" partitions, they have to be the same filesystem. "Mass Memory" is NTFS, the other spaces are not. If you want a single data partition (Mass Memory), then you should copy the contents of the other partitions into Mass Memory, remove the other partitions, and when everything has been copied, resize Mass Memory to take up the unallocated spaces.

---

