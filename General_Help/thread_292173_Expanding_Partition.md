---
title: "Expanding Partition"
date: 2006-11-03
forum: General Help
---

### Post by thekingof7 on 2006-11-03
So I installed ubuntu about 2 weeks ago, and my I jsut say I love it, windoze can suck it. But now I am runnign out of space on my linux partition, I have a 40 gig area of unpartitioned space, is there any way of expanding my ubuntu part. into that space? Thanx

---

### Post by Roobert on 2006-11-03
Where is the unallocated space in relation to your linux partition? If it is after your linux partition, I'm pretty sure you can format the unallocated space as the same filesystem as your linux partition in gparted; if the space is before your linux partition, I don't think there is an easy way to do it. 

You'd have to format the unallocated space as filesystem ext2, say, copy your linux partition into it (if it will fit), then delete your old linux partition, then expand your new linux partition into this freed up space. 

I have this situation where my XP partition is the first partition on my disk, and is too big for my liking, but I'm too afraid to srhink it in gparted for fear of rendering it unbootable.

---

### Post by thekingof7 on 2006-11-03
Well I can move the partiton anywhere I want to (using Hiren's) so where would you recommend I put it? And then what you recommend I do.
btw as for your fear of shrinking it, dl Hirens boot cd, and use acronis part. manager and then you can resize it without fear (I did the exact same thing)

---

### Post by Roobert on 2006-11-03
What's Hiren's? I not familiar with it.

---

### Post by Roobert on 2006-11-03
See [this thread]("http://www.ubuntuforums.org/showthread.php?t=244233&highlight=Expanding+linux+partition"); it seems the poster was having the same issues as you. It's explained probably better than I can do it.

---

### Post by dcstar on 2006-11-04
> **thekingof7 said:**
> So I installed ubuntu about 2 weeks ago, and my I jsut say I love it, windoze can suck it. But now I am runnign out of space on my linux partition, I have a 40 gig area of unpartitioned space, is there any way of expanding my ubuntu part. into that space? Thanx

You can boot off the Ubuntu Live CD (or any of the other Linux utility boot CDs around), and then use the Partition utility to expand your (currently unmounted) partition into adjacent spare HD space.

Otherwise set up a new partition, and use the partimage utility (after booting up from a CD) to move your existing partition into the new one.

---

### Post by thekingof7 on 2006-11-04
Well I did, I used Hirens all-in-one boot cd, and acronis disk director (which was already on the cd) I jsut clicked resize partiton, and expanded it into the un-used space. It was very easy.

---

