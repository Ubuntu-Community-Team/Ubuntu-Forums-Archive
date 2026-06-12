---
title: "Partioning single partition after installing ubuntu"
date: 2007-09-28
forum: General Help
---

### Post by aLT Wizard on 2007-09-28
Good Day,
I have ubuntu installed on a 40 GB Harddisk on a single partition. I have 17 GB Free on the partition and would like to install xp for dual boot after partitoning the free 17GB into 10GB for ubuntu and 7GB for windows xp. Is that Possible??

---

### Post by overkillm on 2007-09-28
If you have an Ubuntu LiveCD you can boot to it and use the gparted tool to partition your hard disk any which way you like.  I believe Windows likes to be on the first primary partition, though, so you may need to rearrange the order of the partitions.  Gparted can do this with no problem.  If you don't have an Ubuntu LiveCD, the gparted LiveCD is a great resource to have:

[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

However, I would advise against partitioning your disk in such a way that each partition is completely full.  You'll run into performance issues, especially on the XP partition.  From your post it sounds as if your Ubuntu install is taking up 23 of the 40 GB and you want to max out the remaining 17 by making two new partitions.  You always want to have some free space on each partition.  If I've misunderstood, forgive me.  :)

Oh, and also: Be sure you make good backups of your data before messing with the partitions.  Always a smart precaution.
'nother edit: I fogot, Windows has a delightful tendency to wipe out any other OS present during install.  DEFINITELY backup first, if your drive doesn't already have Windows. Then partition accordingly, install Windows first, and then restore your Ubuntu backup if it gets hosed.

---

### Post by aLT Wizard on 2007-09-30
Thanks alot !

---

