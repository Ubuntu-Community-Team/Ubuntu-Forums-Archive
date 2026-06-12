---
title: "Calculating size on disk vs real size."
date: 2018-01-29
forum: General Help
---

### Post by CombatGod on 2018-01-29
So I had to run PhotoRec to restore some image files. Of course those image files now have no filenames.

I do have logs with all the filenames and of the size.

However, the size in the logs is always bigger than the actual size on disk. However, I can't file the life of me figure out the equation.

Somebody smarter than me plz help.

So I found some of the actual files and got their size on the disk and included the size of them in the logs:

Logfile Size:                         Size on Disk (searchable size):
212572bytes * .998856858 = 212329bytes
159223bytes *  .998473839 = 158980bytes
122661bytes *  .99801893 = 122418bytes
98593bytes *   .997545465 = 98351bytes
78328bytes *   .996910428 = 78086bytes
51373bytes *   .99530882 = 51132bytes
44145bytes *   .994540718 = 43904bytes

What am I missing? I can see that the multiplier goes up slightly with filesize but I can't come up with an accurate equation to get the actual size on disk and do a search. PLEASE PLEASE PLEASE help!

---

### Post by oldfred on 2018-01-29
Do not know.

But is one drive the newer 4K and the other older 512?
Then data may be taking up more space on 4K sectors?

       First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by CombatGod on 2018-01-29
No both drives are on an ext4 system with the same block sizes.The size on the disk is the same for both files. 

However, it's the size in the logs that gives the actual filesize not just the size on the disk.

---

### Post by CombatGod on 2018-01-30
Does anybody know the calculation for getting the difference between the size on disk and file size reported?

---

