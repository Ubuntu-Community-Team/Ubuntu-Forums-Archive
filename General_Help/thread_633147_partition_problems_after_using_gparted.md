---
title: "partition problems after using gparted"
date: 2007-12-06
forum: General Help
---

### Post by billgoldberg on 2007-12-06
I don't know if this is posted in the right subforum.

My computer had 2 partitions, a 70gb ubuntu gutsy, and a 10 gb xp. As almost all my data from ubuntu is on an external hd, it only was around 4 gb big.

Xp was constantly begging for more harddrive space. So I popped in Gparted.

I repartitioned both drives to 40 gb.

After paritioning I log into xp, check the disk managment (could be called different, mine is called "schijfbeheer").

It said, xp was 40 and another "unknown parition was 40 gb.

So i had more space. I tried downloading something, xp told me it didn't had enough space.
I right clicked the c-drive, there still was only 10 gb available, even if "disk managment" and gparted said it was 40. Rebooting didn't help.

How can i fix this?

---

### Post by kelvin spratt on 2007-12-06
Force Xp to do a disc check right click on the drive select tools select check for errors click both boxes follow instructions. That will check every thing on that partition.

---

### Post by ryanVickers on 2007-12-06
did you just expand the partition or make a new one?  All new partitions need to be "initialized" in Disk Management and then formatted again, even if you did this in gparted...

---

