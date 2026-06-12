---
title: "partition resizing question"
date: 2007-11-02
forum: General Help
---

### Post by benner on 2007-11-02
if i use gparted to resize a partition (enlarge it) how likely am i to lose the data in the partition?  i remember once i combined two partitions and lost everything in both so i am a little gun shy.  but i have no other place to put this stuff.  i have a 250 gig disk that i want to put a fresh install of gutsy on.  currently there is a 69 gig partition with an old xp install that i am ready to kill and a 92 gig partition with a 32-bit feisty that i am ready to get rid of now that 64 bit is a bit more mature.  so the remaining 69 gig partition is my data storage that i  would prefer not to lose.  
i wanted to have the OS on one partition and the home folder in another and the rest for data, downloads etc...  how much would you recommend for the OS and how much for the home?  
thanks in advance...

---

### Post by Ramorous on 2007-11-02
I recommend you boot into the live CD to make sure none of the drives are mounted and being used.
Followed by using gparted to resize. I've resized several drives using Knoppix live cd (you can use K/ubuntu as well). When resizing, don't use up 100% of available space, just take away a few MB from the end.

---

