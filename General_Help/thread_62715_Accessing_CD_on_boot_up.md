---
title: "Accessing CD on boot up"
date: 2005-09-05
forum: General Help
---

### Post by wadesmart on 2005-09-05
09052005 1523 GMT-5

Long story short, I have run out of space on my current partitions and my requests for help in numerous forums have not help me at all. I have tried parted but have too many questions and not enough answers. 

I read that you can use the ubuntu install disk and access the partition information that way and resize the partitions. But I cant get the CD to boot when the system starts up. 

How do you get a cd to run instead of the OS? My cd is first in the bios for startup. 

Wade

---

### Post by plb on 2005-09-05
you bios should be the one detecting the cd not ubuntu, personally I would recommend using knoppix as it has many utilities and use something like qtparted(I believe thats the name) to redistribute space amongst your partitions

---

### Post by wadesmart on 2005-09-05
09052005 1800 GMT-5

BIOS has CD first but upon boot its not even spun up. 

I dont have any more room to download anything. I have literally 1mb or less right now on /home. Im started to become worried that the cache of Firefox will cause me problems as well. 

Thanks on that though. 

Anyone else know anything about parted? 


Hey, let me ask you this then. I was going to use parted but Im having all these problems with it. One problem is that I have to unmount the partitions before resizng them. Well, if one of the partitions that Im resize is /var and I you cant unmount it while your one the computer, how can you resize it? 

Wade

---

### Post by wadesmart on 2005-09-05
09052005 1944 GMT-5

If I get some room to download and burn Knoppix, can one os cd be used to partition another? And how would I go about this? 

Wade

---

### Post by Irony on 2005-09-06
I'm new to linux but I installed gparted and found it very easy to use - it represents the partitions in an easy to view GUI way and by clicking/right clicking on the partition you have options to format as a different type or resize.

I don't know it the ubuntu liveCD has gparted but if it has that may solve your partition problems.

---

