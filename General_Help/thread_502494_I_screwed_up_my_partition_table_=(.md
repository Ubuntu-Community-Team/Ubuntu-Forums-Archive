---
title: "I screwed up my partition table =("
date: 2007-07-16
forum: General Help
---

### Post by roach of discord on 2007-07-16
This isn't exactly ubuntu related, so move if needed :).

I recently did a command to remove my mbr (bad idea?)..because windows wouldnt install, it kept complaining, and I found out that my mbr was probably messed up. THat worked, however, windows installed (recovery cd) without even asking me about a partition.  I think it formatted over one of my important partitions too =(.  It seems I can't recover any of my data either...which horribly sucks.  I had tons of important stuff on that partition.

Anyway, I have 3 other partitions as well.  They are no longer showing either.  However, I downwloaded a partition doctor program, and it shows that they are infact still there, once I fix the MBR.  Infact, when i launch the program it says "Error: Partition table doctor has detected MBR on harddisk 2 was broken. The right MBR on harddisk 2 is sector 0 0 8 (chs), do you want to correct this error?"  Then it also says "Error: Invalid boot indicator of primary partitions on harddisk 2, do you want to correct this error?"  If I choose yes to both, it fixes it and I can see my partitions with this tool.  I can actually even browse one of them, but can't copy anything from it.  

This would be great though..but the program is an expensive tool and I only have the demo. It won't let me save the changes without paying loads of money.  Is there anyway I can fix my partition tables, some how?  I really want my data back :(.  I'm not sure what screwed everything up..if it was windows or the mbr command..but it's bad.  If anyone can help me to get those partitions to show, i'd be very greatful.  They don't show in fdisk or cfdisk..and im guessing because of the errors i posted above.  If I could fix those, without that program..i'm guessing they would be accessable again.

Currently I am using windows, and I have an ubuntu livecd.

Thanks
-RoaCh

---

### Post by jasonlfunk on 2007-07-16
What is the output of ```
df
``` in the terminal while in the Ubuntu Live CD?

---

