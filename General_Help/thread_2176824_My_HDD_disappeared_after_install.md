---
title: "My HDD disappeared after install"
date: 2013-09-26
forum: General Help
---

### Post by kristian_brasel on 2013-09-26
o boy... i have windows 8 on my 1st ssd and i installed ubuntu on a 2nd ssd and now i cant see my hdd in windows or ubuntu. in windows i looked in the disk manager, its not there, and in control panel i looked in storage spaces and it says its disconnected or inaccessible. during installation i selected new partition table for my 2nd ssd because it wasnt seeing any of the free space. i created a 15GB / partition and a 25GB /home partition and now i cant even see the /home partition in ubuntu. somebody please tell me its a fairly simple fix. im lost.

---

### Post by theDaveTheRave on 2013-09-26
Kristian,

I guest you are using a 'live CD', if this is the case the settings are lost between boots, so you aren't going to automatically see your other HDD (it won't be mounted).

If this is the case follow the instruction on the ubuntu wiki for [liveCD persistance]("https://help.ubuntu.com/community/LiveCD/Persistence").

Othersiwe you'll need to run some other investigations. First off start with
```
more /etc/mtab
```
then try
```
more /etc/fstab
```

This will tell us what disks are available, and if they are automounted or not.

Also can you tell us what your hardware is, you make is sound as though you have 3 disks available. One for your main OS (either windows or Ubuntu), and a 3rd that is 'inside' your hardware. I'm guessing you are using a chromebook / netbook or something similar?

David

---

