---
title: "Unallocated partition data?"
date: 2006-10-24
forum: General Help
---

### Post by Vekemi on 2006-10-24
I figured that one of my partitions had too much free space that I didn't really need, so I decided to use gparted to remove some of that free space.

However, the free space is under /dev/sda4 now and it won't let me put it to /dev/sda2 where I want it to be, so now I have 30 gigs of unallocated data.

If it means anything, /dev/sda2 is an ntfs drive.

---

### Post by mjziegle on 2006-10-24
Your data has to be in continuous sectors in order for it to be in the same partition or device.  

What you did was strip off the edge of /dev/sda3.  This piece of the drive isn't continuous with /dev/sda2.

Everything is working as it should.  

If you want to expand your ntfs partition you'll have to move the data from /dev/sda3 to /dev/sda4 and then bond /dev/sda2 with /dev/sda3

I couldn't recommend doing this with an ntfs partition unless you care very little about your data.

---

### Post by CatKiller on 2006-10-24
Actually, I think the OP should be able to slide sda3 to the right to make the space available to extend sda2. But I concur that he must back up the data that he doesn't want to lose.

---

