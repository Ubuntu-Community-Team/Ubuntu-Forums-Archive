---
title: "Ran out of space (partition problems)"
date: 2017-02-21
forum: General Help
---

### Post by ionimpulse on 2017-02-21
Hey everyone!
I recently installed Ubuntu with a partion size of 10 gb. I now want to increase the partion to 20 gb, but gParted and windows disk mangement won't work. So my question is, can i delete the 2 "recovery" partions in between the Ubuntu and Windows partions?

---

### Post by oldfred on 2017-02-21
Do you have good full image backups of Windows? And all your data?

My Dell had Windows recovery & Dell recovery, and after I ran those backups, it offered to delete recovery partitions. But I also used Macrium Reflect to make full image backup.
 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)
Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media) 


You have to use live installer's gparted or download the gparted ISO and boot that. You cannot edit or move mounted partitions.
I do not like moving partitions left which you have to do as then you expand right. If you do make absolutely sure you do not interrupt the process. Any interruption or power failure totally corrupts partition and only recourse is reinstall & restore data from backups. The larger the partition and the more data you have the longer it takes to move a partition.

---

### Post by ionimpulse on 2017-02-21
I just installed Ubuntu on this computer. Would it be easier (and less risky) to just uninstall and reinstall Ubuntu, this time with more space?

---

### Post by Bucky Ball on 2017-02-21
Yea, that would be easy. One other thing is, don't use Win Disk Management to try and resize Ubuntu/Linux partitions. Other thing is, you need to run from a 'live' session to resize the Ubuntu partition using Gparted. You can't resize a running Ubuntu partition, as oldfred said. ;)

---

