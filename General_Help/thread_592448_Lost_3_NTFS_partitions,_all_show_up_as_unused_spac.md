---
title: "Lost 3 NTFS partitions, all show up as unused space"
date: 2007-10-26
forum: General Help
---

### Post by chameleon_789 on 2007-10-26
Basically, I was stupid :( 

Basically, I had 3 NTFS and a linux ext3/swap partition on my hard drive. Vista stopped booting and ubuntu stopped detecting my NTFS partitions, so I stuck in a copy of Hiren's boot cd which I had lying around and ran Partition Magic, which informed me that the boundaries of the partitions were incorrect, and that it could automatically fix them... except they weren't, and I let it fix them, and now all of the NTFS partitions are listed as unused space in all the partition tools I try, including the two partitions that were adjacent to each other, and the one after the Linux partition.

I've tried to repair the table using other tools on Hirens boot CD, but none of them detect the NTFS partitions. I also tried testdisk, which only detects the ext3 and swap partitions, and then hangs at 88% (I'm guessing this is the end of swap/start of the third ntfs partition). I also tried using a Vista install disk to repair but it hangs before I'm able to get to the automated recovery menu.

Usually by this point I'd give up and reformat, but I've got a lot of work I really can't afford to lose which is scattered around all three of the partitions. Is there another way of recovering the partition table, or am I relegated to data recovery software (if so, can anyone recommend some)?

---

