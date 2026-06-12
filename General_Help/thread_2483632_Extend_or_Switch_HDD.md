---
title: "Extend or Switch HDD?"
date: 2023-02-05
forum: General Help
---

### Post by cryptognome on 2023-02-05
Hey All,

Hopefully this is the right place to post.

I have been messing with Ubuntu on an old thin client I managed to get my hands on. The downside to using such a basic machine is the storage solution. Currently a 16GB SSD.

Long term I am going to switch the thin client for something more purposeful but in the meantime it is doing well for what I need.

My issue is I have now hit the wonderful 16GB limit! Yay! Luck me! 

I have a 1tb USB 3.0 HDD that I would like to use to extend the primary system partition so I can actually perform some updates. 

I am trying to avoid having to start from scratch re-installing the entire OS onto the new drive. In windows I know how I could do this very easily but I am not quite to sure about Ubuntu.

Is there an easy way I can tell Ubuntu to use this drive as extra space in general?

I have heard of gpart and thought maybe I could just do a copy paste and will be well?

Kind of at loss to get started on this any advice would be great!

---

### Post by oldfred on 2023-02-05
You can move /home or move just the data in /home. The settings in /home in hidden . files are small, except for Firefox & Thunderbird, perhaps some others.
Since 16GB is small, you also need to regularly houseclean. I run an update & houseclean script to remove cruft. And some like logs and caches that may have size limits can be partially housecleaned or limits reduced. 

You still should have good backups of at minimum /home, list of installed apps and any edits you may to system files usually in /etc.

To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving) & 
[https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437](https://ubuntuforums.org/showthread.php?t=2455822&p=14010437#post14010437)

[https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909](https://ubuntuforums.org/showthread.php?t=2464944&p=14048909#post14048909)
[http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198) &
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

I recently updated my system. I built it back in 2016 with a M.2 SSD as NVMe drives were very expensive then. I wanted larger & also changed to NVMe drive. But to use M.2 SSD, I bought a M.2 to USB adapter and found it almost as fast as it was when an internal drive.

---

