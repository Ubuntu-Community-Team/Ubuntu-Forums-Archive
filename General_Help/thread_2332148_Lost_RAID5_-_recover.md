---
title: "Lost RAID5 - recover?"
date: 2016-07-28
forum: General Help
---

### Post by Forbees on 2016-07-28
so.... i accidentally unplugged two of my three 2TB drives in my RAID5. when i plugged them back in my super block was missing, on all drives, and i was unable to assemble the raid. after a few hours of trying to figure out how to get around missing super blocks i found someone that said if i just create a "new" RAID5 from the old drives it'll just magically work, so i tried it and you can guess it didn't work

currently i've been trying to get TestDisk to work at recovering the partition table of my "new" RAID5 so i can get the data back. only problem is every time i try running it, even after deeper scan, it says the partition can't be recovered. i made this RAID a few years ago and for the life of me i can't remember why i decided to let it be an NTSF instead of EXT4, and i'm afraid that might be why TestDisk isn't working


any suggestions? i'm going on day 3 and i don't want to call it quits, i had this RAID almost full with all my movies and music, it'll take months to get it all back without data recovery 
i hope i attached the screen shots right. one shows the partition i'm trying to save, one shows what happens after i hit continue, listing the partitions it'll let me save, which are garbage 
[ATTACH=CONFIG]270418[/ATTACH]

---

