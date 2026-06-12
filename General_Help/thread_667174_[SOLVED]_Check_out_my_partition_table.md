---
title: "[SOLVED] Check out my partition table"
date: 2008-01-14
forum: General Help
---

### Post by sofasurfer on 2008-01-14
When I used Debian I had no problem creating partitions for home, usr, etc, swap, var.
Now, with Ubuntu I was offered auto partitioning, which gave me / and swap only, and I was also offered to do it manually which I did but then my system would freeze on the splash screen. So, here is what I ended up with...

 Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        6497    52187121    7  HPFS/NTFS
/dev/hda2           11683       19929    66244027+   b  W95 FAT32
/dev/hda3            6498       11464    39897427+  83  Linux
/dev/hda4           11465       11682     1751085    5  Extended
/dev/hda5           11465       11682     1751053+  82  Linux swap / Solaris

hda1 is windows, 2 is just a partition I formated to keep it from being used when I told Linux to used the largest free space, 3 is Ubuntu /, 4 is unknown to me since I did not create it as far as I know, and 5 is Ubuntus swap space. 

Here are my questions...
Since I can save any directory to DVD that I want, is there any reason why I would be concerned with only having the / and swap partitions? 
What would be the advantage to having seperate usr, var, home and etc partitions? 
Can a present system have more partitions added to it for the purpose dividing the system into more peices?
 
My / partition is approximately 38 gig and swap is approx 2 gig.
Do you recommend changing anything or is the current setup adequet?

---

### Post by erpo on 2008-01-14
The older than dirt standard for partitioning disks only left room for 4 partitions. In order to section up the disk into more partitions, you can create an "Extended" partition, and then slice *that* up as much as you want. The fifth partition is actually inside the fourth partition. You could slice /dev/hda4 into sixty partitions if you wanted to.

```

Whenever you cut and paste from the console, put it inside code tags so it looks like this.
Then it will display properly for people trying to help you.
```

In order to get information about the advantages and disadvantages of multiple partitions, google for advantages and disadvantages of multiple partitions. You will find a web site like [http://www.hal-pc.org/journal/2006/06_july/feature.html](http://www.hal-pc.org/journal/2006/06_july/feature.html) that will explain it

I recommend one big partition. It's simpler and IMHO leads to fewer headaches later on.

---

