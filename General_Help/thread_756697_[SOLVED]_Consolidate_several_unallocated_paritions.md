---
title: "[SOLVED] Consolidate several unallocated paritions"
date: 2008-04-16
forum: General Help
---

### Post by Crusty Juggler on 2008-04-16
I am trying to migrate my /home to its own partition in anticipation of the Hardy release.  Problem is, I can't seem to consolidate the several unallocated partitions on my drive.  I'm starting to think maybe backing up my /home directory, adding it to its own partition and formatting the Gutsy partition when I install Hardy may be the go.

---

### Post by TeoBigusGeekus on 2008-04-16
You have to use the gparted live cd 
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
to perform any changes to your system, because hard disks need to be unmounted first in order for the application to do anything.

---

### Post by prshah on 2008-04-16
> **Crusty Juggler said:**
>  Problem is, I can't seem to consolidate the several unallocated partitions on my drive.  I'm starting to think maybe backing up my /home directory, adding it to its own partition and formatting the Gutsy partition when I install Hardy may be the go.

Holy hell, that's one hell of a partitioning scheme. 

Your problem is that your unallocated space is scattered between the primary and extended partitions. Unallocated space in the extended partiotion (/dev/sda4) cannot be consolidated with space "outside" the extended partition. What you need to do is shrink the extended partition; this will "push" the unallocated space into the "primary" area. You can then move your partitions up or down to consolidate the free space.

All in all, shrinking an EXTENDED partition is RISKY. You would be better off with your second idea.


> **TeoBigusGeekus said:**
> You have to use the gparted live cd 
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")
to perform any changes to your system, because hard disks need to be unmounted first in order for the application to do anything.

He _is_ using gparted and since the partitions are unmounted, I guess he is using it from the live CD

---

### Post by Crusty Juggler on 2008-04-16
> **prshah said:**
> Holy hell, that's one hell of a partitioning scheme. 

Yes, unfortunately, I didn't have a firm grasp on how the partitions would work when I set it all up...

> **prshah said:**
>  All in all, shrinking an EXTENDED partition is RISKY. You would be better off with your second idea. 

Sounds like that is the easiest and safest route.


> **prshah said:**
>  He _is_ using gparted and since the partitions are unmounted, I guess he is using it from the live CD

Yes, that is correct.  Thanks for the help!

---

