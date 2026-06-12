---
title: "Broken Hard Drive Recover Help"
date: 2007-01-21
forum: General Help
---

### Post by toran on 2007-01-21
ok, so I'm having some serious hard drive problems- errors, switching fs to read-only mode, and such. So I'm trying to fix this drive, and i run fsck on it. Now when I mount it to get to the data all that on it, all that i see on it is a lost+found directory with maybe 100 files, and maybe a few other things (not directories) in the top level. This drive had over 180gb of stuff on it. Is there any way to recover any of this stuff? Note that when I look at the disk with a partitioning program, it says the disk is 180gb full.

---

### Post by jpeddicord on 2007-01-21
I looks like the Ext3 filesystem may have broken down. All of your files that are lost should be in the lost+found directory, though I am not entirely sure what to expect in there.

Good luck trying to recover the files (not sarcastic); it sucks when hard drives do that. Did you shut off the power when it was moving a big file or checking the disk?

---

### Post by toran on 2007-01-22
Thanks for replying.

Upon closer inspection, I found that lost+found contained about 80gigs of stuff (My drive had about 170gb of stuff originally.) 

It turned out that the only really useful thing salvaged was my music collection, which was, interestingly enough, completely intact. While I probably would have had a great deal of trouble replacing it, it wasn't my most important files. There isn't really anything I can do, though.

As a side note, I would NOT recommend Western Digital drives to anyone. I bought a 200gb SATA drive from them about 2 years ago, and it began failing. I caught it and backed up it, and got it replaced May 2006. The drive that I just had fail on me was the replacement sent to me by WD.

BEWARE.

---

