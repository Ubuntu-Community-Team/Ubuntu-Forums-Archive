---
title: "Broken partition - Please help!"
date: 2005-09-28
forum: General Help
---

### Post by AdmiralSenn on 2005-09-28
I have a very bad problem...

I recently switched to Ubuntu almost 100%, only loading XP on rare occasions. Because of this, there were some extra programs on XP that I didn't need anymore, and a lot of duplicated personal files (these files were on a FAT32 drive so both OS's could use them). I deleted the duplicated files on the NTFS partition and, being an idiot, decided to use Partition Magic 8 to resize the NTFS partition and allocate the extra space to my FAT32 partition. 

In the course of this, I had to restart, and then PM froze on me about a third of the way through the resizing process. I left it for half an hour; when it was still at 31% I restarted the machine. I reloaded PM8 and managed to redo those modifications after some work - I had to fix the boot record for Windows. Suddenly GRUB stopped working - Error 17 - and I had to fix the master boot record to get anything working at all. 

Unfortunately, now my ext2 partition, while it's still there, is inaccessible. GParted sees it, Partition Magic sees it, but they can't do anything to it except format it, and that I cannot and will not do. Also, probably as a result of the broken superblock, the partition is listed as having exactly the same amount of data it contains - so both capacity and actual size are the same number. Ext2fs keeps telling me the superblock is broken, too.

Thinking I could somehow fix this, since nobody I talked to had any bright ideas, I made a second ext2 partition out of some free space. Now Partition Magic doesn't work at all, and any fixing I do will have to be from my Live CD, which is how I've been working on things.

Long story short, I basically need to do the equivalent of reformatting this partition without losing any of the data that's on it.

Thanks in advance. I don't even know if I can back up the stupid thing - I only have a 20 gig drive to use for backup, and while I only have about 16 gigs of storage on the partition, the size is closer to 27 gigs, and if I can't find individual files on it to save, or some way to compress it, then I'm out of luck.

---

