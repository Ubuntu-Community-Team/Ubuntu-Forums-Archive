---
title: "Strange partitions gutsy windows dual boot"
date: 2007-11-29
forum: General Help
---

### Post by tom1979 on 2007-11-29
Finally got gutsy installed on the easynote as i want it, minus wifi,  but noticed when i was partitioning i didnt have a lot of space to work with as windows appears to have partitions already.

in Gparted now im seeing 
hda1 5.94gb fat32 flagged hidden
hda3 19.84gb ext3
hda4 721mb swap
hda2 20gb ntfs label HDD flagged root
7.84 mb unallocated

ive just shrunk the hda2 and stretched hda1 and hda3 as both were extremely low on space and i was only able to partition the ntfs part when i installed. 

Im curious as to what windows has a hidden fat32 partition for with 3gb of data, i cant see it from windows, or clearly in gutsy.

As my ubuntu install was far from simple this time i dont want to run a clean install of both windows and gutsy, but i would like to lose the partition if possible and increase the hda2 or hda3.

also on my other installs ive only had hda1 as windows, hda2 as ubuntu, and hda3 as swap, infact thinking about it my clean install of gutsy and windows on my think pad has strangely labeled partitions too...

any ideas?

---

### Post by ijason on 2007-11-29
i this windows vista? i keep hearing that windows vista does strange things with it's partitioning. the small 3gb partition may be dedicated for windows swap.

when i set up a machine with dual windows xp and ubuntu, i had 3 partitions. windows, ubuntu, and ubuntu swap.

---

### Post by kylecchh on 2007-11-29
What type of PC do you have? It may be a backup partition for Windows. My HP has the same exact size partition for backup

---

### Post by ptn107 on 2007-11-29
If you bought your PC from a vendor then the hidden partition may be a recovery partition for windows.  Many vendors do this now so they don't have to ship CDs or DVDs with the computer (they want to cut down total cost of production).

---

### Post by Teknyk on 2007-11-30
> **ijason said:**
> i this windows vista? i keep hearing that windows vista does strange things with it's partitioning. the small 3gb partition may be dedicated for windows swap.

when i set up a machine with dual windows xp and ubuntu, i had 3 partitions. windows, ubuntu, and ubuntu swap.

I hope that isn't even Vista Home Basic on that 20gb partition much less any other version of Vista. That barely meets the recommended system requirements.

More likely that is what ptn107 suggests it is. A hidden recovery partition. I had a similar layout when I was dual booting my XP/Ubuntu.

---

### Post by tom1979 on 2007-12-03
No im still using windows XP ... ok ill leave that 3gb alone as the laptop seems to be running ok at the mo...

---

