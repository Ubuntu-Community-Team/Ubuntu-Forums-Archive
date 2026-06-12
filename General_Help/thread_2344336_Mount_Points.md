---
title: "Mount Points"
date: 2016-11-24
forum: General Help
---

### Post by Quarkrad on 2016-11-24
Just installed Mate 14.04 to my / partition.  Previous to this I had Mate 16.04 in / and a separate /home partition - in /home I had the standard folders, Downloads, Documents etc.  During the 14.04 install I reformatted / but did not reformat /home as I wanted to keep my folders/files intact.  All is OK except the 14.04 install has created a new mount point called 105 GB (listed under Devices in the caja file manage window).  What has happened is that the new install is under /home and my previous user has been put under /media (i.e. /media/usersname/40AC82...../username/Audio, Desktop, Documents, etc.  Where 40AC82... is the UUID of the correct partition). Additionally I have another HD that has also been mounted under /media.  What is the simplest way of getting rid of the empty standard folders (Desktop, Downloads, Documents, etc) under /home and replacing them with what is now under /media?  Is all this controlled through fstab - do I just type in what I want and it will all appear as before?  (Sorry - always struggled a bit with mount points).

---

### Post by TheFu on 2016-11-24
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Use **blkid** to get the UUID to device mapping. Can't tell you what to type.  Did you make a backup of the prior install /etc/ before starting over?  That fstab would have had the info you needed., probably.

---

