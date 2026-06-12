---
title: "Configuring BackInTime-qt4"
date: 2022-03-06
forum: General Help
---

### Post by wyattwhiteeagle on 2022-03-06
In my search for configuring BackInTime-qt4, I found this guide...
[https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/](https://www.howtogeek.com/110138/how-to-back-up-your-linux-system-with-back-in-time/)

I also found the page which say's that the configuration file needs to be configured manually and directs the user to /etc/share/ directory archive example file.
(Which I've failed to successfully open the file to see the example)

It seem's that when I look at example's it leaves more confusion instead of clearing up confusion.

The above link leaves me with some questions...

Under the General tab, it say's "Where to save...". The link shows "/home/HowToGeek/Backups". 
Mine is blank.

Do I just type something in there?
Where is a good place to keep the BackInTime backups?
Do I need to "create" the directory?

---

### Post by TheFu on 2022-03-06
I haven't looked at Back-in-time in about 8 yrs.

As for where to store backups, the rules are always the same.
[LIST]
[*]Different storage device
[*]The location of the backup storage isn't included in the places that get backed up (seems obvious).
[*]Using a file system as required by the software - back-in-time needs a POSIX file system
[*]all the advanced consideration are the same as for other backup tools.
[/LIST]

Back-in-time is basically an rsync + hardlinks solution. rsnapshot is similar (without a GUI).  Hardlinks mandate that the backup storage support Linux file systems - ext2/3/4, zfs, xfs, jfs, or 10 others will work fine.  Not NTFS, not any FAT-based file systems.

---

### Post by GhX6GZMB on 2022-03-06
Dunno why you're focusing on "-qt4".
Backintime is what it is and works wonderfully. I use it myself for user file backups (/home). No reason for big configuration file actions.
So just install it and run it. That should work.

---

