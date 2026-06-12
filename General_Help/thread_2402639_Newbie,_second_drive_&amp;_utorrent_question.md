---
title: "Newbie, second drive &amp; utorrent question"
date: 2018-10-02
forum: General Help
---

### Post by deanoandrew on 2018-10-02
Hi People. 
I had an old machine running windows XP with 2 hard drives a 70gb system drive and a 2tb data drive. 

I have done a clean install of ubuntu 16.04.5 on the system drive and all is well, i have installed utorrent, and i am trying to connect it to my existing torrents and data sitting on the data drive.  However whilst i can still see my data folder in ubuntu( it shows as Storage ) i can not access those directories from Utorrent.  I assume because they were originally windows directories. 

Any advice will be appreciated, please note my PC knowledge is very limited, i can monkey see monkey do, so please do not hold back with the ubuntu made simple for idiots :p

Many thanks
Dean

---

### Post by mastablasta on 2018-10-03
> **deanoandrew said:**
> 
I have done a clean install of ubuntu 16.04.5 on the system drive and all is well, i have installed utorrent, and i am trying to connect it to my existing torrents and data sitting on the data drive.  However whilst i can still see my data folder in ubuntu( it shows as Storage ) i can not access those directories from Utorrent.  I assume because they were originally windows directories. 


windows file systems (by default) are not automatically mounted. they mount when you click on them in "files".

[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

[http://csetutorials.com/auto-mount-ntfs-partitions-startup-ubuntu-linux.html](http://csetutorials.com/auto-mount-ntfs-partitions-startup-ubuntu-linux.html)

---

