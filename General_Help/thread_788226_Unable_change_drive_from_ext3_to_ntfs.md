---
title: "Unable change drive from ext3 to ntfs"
date: 2008-05-09
forum: General Help
---

### Post by Pjcity on 2008-05-09
Hi all, 

I have added a 750Gb drive for storing media onto Ubuntu 8.04 by partitioning and formating it with Gpartition but I have partitioned the drive with one large partition as ext3, now I didn't realise that you could partition and formating with ntfs and be able to run the drive with windows as well as Ubuntu...

Now I can't reformat and partition the drive with Gpartition to ntfs as this option is shaded out when you bring it up ......

Any thoughts as I want to have the drive as ntfs if poss before I start adding any media ?????

---

### Post by markharding557 on 2008-05-09
if you get a copy of the gparted live cd you can format to ntfs on that but if you want to install windows it would better to use the windows installer to format.
installing windows will remove grub but you can restore this using an ubuntu live cd

---

### Post by eriqjaffe on 2008-05-09
You can acces ext2/3 filesystems from Windows, you just need a driver to do it.

[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)

---

### Post by Pjcity on 2008-05-09
Cheers for the info, 

I just thought If I could format the drive to ntfs now it would save work later but I suppose I could always use fs-driver when or if I need to access the media drive from a windows pc in the future....

For the record the drive is an additional storage drive I am going to use as part of a server to stream media around the house so it's probably not going to be accessed by windows unless it's moved to another pc which is unlikely...

---

### Post by drthompson on 2008-05-10
I've been struggling with the same thing and installed Heron on an external USB drive only to find that it would not recognize it and boot.  So, now there were 2 partitions, one NTSF the other ext3.  On the NTSF I had mirrored My Docs, I could loose it but would rather not, my problem was Heron had taken up all the remaining space (about 200gb) in the ext3 partition making it unavailable to me in Windows.  I found Paragons Partition Manager and gave it a try, worked great, I was able to reformat the ext3 to NTSF and then extend the primary partition to recover all the space into one big volume for backups again.  It's a pretty slick program & also has a boot manager wizard which I'm going to try today.

---

