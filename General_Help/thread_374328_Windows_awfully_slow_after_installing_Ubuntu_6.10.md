---
title: "Windows awfully slow after installing Ubuntu 6.10"
date: 2007-03-02
forum: General Help
---

### Post by venator260 on 2007-03-02
I just installed Ubuntu 6.10 after having 6.06. I had 6.06 on my slave hard drive. To get rid of it, I simply formatted the Linux partition from Windows, and started again. 

After having trouble mounting a FAT32 partition on my slave drive, I booted into Windows to take the suggestion of a member of this forum about that problem, to defrag and scandisk, to see if that helped. 

I was greeted by a boot up that was painfully slow. This wasn't just a perception shift because of Ubuntu's speed, it really took 2x-3x as long. Then, once I got into Windows (and where my problem differs from the other thread I saw on this subject) is that anything Windows explorer related is also hopelessly slow. The start menu takes about a minute to display, and I double clicked the Recycle bin about 15 minutes ago, and as I was typing this sentence, it, for some reason, appeared, along with Firefox on my taskbar. 

Firefox, however, runs just fine. 

Any thoughts?

---

### Post by milton1 on 2007-03-02
That much of a speed drop on both boot and run sounds like either a corrupt file or bad memory. If you have more than one stick of ram, try pulling one, see if it helps. You can also boot windows without the splash to see where in the boot process it is hanging.

---

### Post by venator260 on 2007-03-02
But Ubuntu runs as normal, which would exclude bad memory, correct?

---

### Post by milton1 on 2007-03-05
> **venator260 said:**
> But Ubuntu runs as normal, which would exclude bad memory, correct?

Yes, that would seem to be correct. You may have a corrupt system file in Windows. That can happen when you do certain things near a Windows machine. (breathing, blinking, etc...)

---

### Post by reggietee on 2007-03-05
I actually have a similar problem, I installed Ubuntu and afterward, while rearranging partitions, it crapped out on me and a seperate FAT32 partition (with all my important data, NOT my Windows partition) was corrupted. 

Since then I've been trying to get back into Windows to run an undelete on any files I may have deleted before moving them to the corrupted drive... too bad it takes forever to load XP now. During boot, scan disk states it cannot scan the non-Windows drive, then takes another 10-15 mins to load into XP. Then I get the same symptoms as above, including being unable to open My Computer to list drives.

I used testdisk to try fixing up the partition tables, and nothing seems to have changed (I need to look into doing it again because I "may" have done it wrong though). I've almost decided to shelve the problem since Ubuntu is working great, but I eventually have to try recovering all my lost data.

Any ideas where the problem comes from?

---

