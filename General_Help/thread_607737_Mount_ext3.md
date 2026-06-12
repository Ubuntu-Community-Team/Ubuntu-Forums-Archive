---
title: "Mount ext3"
date: 2007-11-09
forum: General Help
---

### Post by PhillipJ on 2007-11-09
I've run out of room on my Ubuntu partition and have scrounged 4 gig from an NTFS partition on the same drive but I can't do anything useful with it. I used Acronis Disc Director and initially attempted to merge the new EXT3 partition with my  current ROOT partition but it told me I would need to do *things* to make that partition bootable again. As i'm partway through my final exams for me B.Eng. I don't want to break anything so I just left it as a seperate partition. All good, but I can't do anything with it. I pretty much want to make WINE install stuff there but I'm a complete nub and don't really know where to look for help so any assistance would be apreciated. Thanks.

---

### Post by stephan0h on 2007-11-09
you would need to mount your new partition. you need to define a mountpoint (i,e, an empty directory) and define the mount in /etc/fstab

hope that was the right answer for your question,

stephan

---

