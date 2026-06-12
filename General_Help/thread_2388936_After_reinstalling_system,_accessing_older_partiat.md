---
title: "After reinstalling system, accessing older partiations"
date: 2018-04-09
forum: General Help
---

### Post by jorritTyb on 2018-04-09
Hi, due to an update to the development bionic that went a bit wrong I decided to completely reinstall my system. Basically that meant that I install 17.10 on my SSD drive. However, my other drive was left untouched and the old partitions are still there. Is there a way for me to access those partitions easily? Not sure exactly what magic incantations I have to do to get those partitions mountable. There are both NTFS as well as EXT2 partitions there (there used to be windows on one of the SSD partition, not anymore)

Thanks!

---

### Post by oldfred on 2018-04-09
Is this an internal drive?
Are all partitions one's you always want access to?'
If so then  you can mount with fstab. 
Some partitions I only occasionally want to mount from main working install like another test install, I just label so I know what it is in Nautilus. 

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Create mount point, mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to as I link folders into /home.

Best not to use NTFS unless you have Windows. It will need defrag and chkdsk which you can only run from Windows or a Windows repair disk. And if chkdsk needed then Linux NTFS driver will not mount it.

Also ext2 should only be used on very small partitions with semi-fixed data like a /boot partition, as it does not have a journal.

---

### Post by jorritTyb on 2018-04-09
Yes it is an internal drive. This is a desktop with an SSD and a normal HDD. The SSD is now fresh installed with kubuntu but the HDD still contains old partiations where my old home dir used to be. Also the NTFS was an old windows partition. I made a backup before this install but it is a lot easier if I can simply open up these partitions and restore what I need directly from that. I'll try to edit the fstab for this. Thanks

---

### Post by Dennis N on 2018-04-09
Ext file system partitions should be accessible from Files (Ubuntu file manager):

In side pane, select "Other Locations" at the bottom. The right pane will then show those partitions. If they have no labels, they show like "20 GB Volume". Use right-click menu on these to select desired action.

---

### Post by jorritTyb on 2018-04-09
Oh indeed. I didn't notice that. In fact, even the NTFS partition can be access there! That makes it a lot easier. Thanks!

---

