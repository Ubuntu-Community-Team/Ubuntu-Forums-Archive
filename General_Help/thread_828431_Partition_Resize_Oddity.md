---
title: "Partition Resize Oddity"
date: 2008-06-13
forum: General Help
---

### Post by Stealth on 2008-06-13
Well, I was trying to resize my home partition to install Vista on a little section of my drive. (3 drives, 1 is for XP, 2 is formatted ext3 for storage, 3 has Ubuntu). So Drive 3 is split up into root, home, and swap partitions. I resized the 2nd partition and left 10GB only to find out that Vista needs at least 13 :P So, using the Live CD once again, I went back to resize it a little more, but I keep getting an error. I think it was something like this:
Attempt to read block from filesystem resulted in short read

Now, this is my home partition. Fsck isn't showing errors, and I can boot fine. I was able to resize it once, but now it won't shrink anymore. I deleted the NTFS partition I had created, and was able to **grow** it back to its original size, but now it won't shrink again. Any ideas?

---

