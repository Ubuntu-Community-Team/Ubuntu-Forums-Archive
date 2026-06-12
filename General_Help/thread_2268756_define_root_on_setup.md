---
title: "define root on setup"
date: 2015-03-11
forum: General Help
---

### Post by Phil Binner on 2015-03-11
I am installing XUbuntu on a Samsung % Ultra.  It has a 500gb scusi and a 24GB SSD.  I obviously want the boot on the SSD, but it is a bit small so I would like to put the root on a 450 gb partition on the Scusi, leaving the other 50gb for swap.  I partitioned the discs accordingly and went for an advanced boot.  I can define what the partitions are to be used for, i.e. boot, swap or file system, but when I try to start the install it says I have not defined the root.  

My problem is that I can't see any way of selecting root as a use for the partition.  When I defined the 450gb partition as a file system it did ask me for the boot point, and I selected "\home".  Should I have just selected "\".

I have gone ahead and performed a standard install on the SSD, but I think it has setup the boot, the file system and swap areas all in the 24gb space.  That will probably cause problems soon.

Any help on the correct way to do this please.

---

### Post by kerry_s on 2015-03-11
make the ssd 1 partition, ext 4 mount as root (/ this is the symbol in menu)
put swap on the 500gb hd, 50 gb is to much, just 4gb(4096) is good
make the rest of the drive /home

---

### Post by coldraven on 2015-03-11
> make the ssd 1 partition, ext 4 mount as root (/ this is the symbol in menu)
put swap on the 500gb hd, 50 gb is to much, just 4gb(4096) is good
make the rest of the drive /home
+1

---

