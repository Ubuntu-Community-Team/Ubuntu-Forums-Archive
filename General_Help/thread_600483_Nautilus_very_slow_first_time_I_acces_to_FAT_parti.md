---
title: "Nautilus very slow first time I acces to FAT partitions"
date: 2007-11-02
forum: General Help
---

### Post by Liet on 2007-11-02
Nautilus is very slow (about 10 seconds) the first time I access to FAT partitions, and when it has gone a long time since I had access them.

How can I fix this?

Thanks

---

### Post by FuturePilot on 2007-11-02
Are you running Gutsy? A fresh install of Gutsy? Or upgraded to Gutsy?

---

### Post by grim4593 on 2007-11-02
I have had this problem as well. When I plug in my external usb harddrive and access the FAT partition on it, nautilus freezes for about 30 seconds before showing the directory. It never did this until I upgraded to Gusty. I also have an EXT3 partition on the external drive, and it loads as soon as I open the folder.

I upgraded to 7.10 from 7.04.

---

### Post by FuturePilot on 2007-11-02
Well this seems to be the problem.
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567]("https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/133567")
However this was fixed. But if you added a FAT partition/drive manually to fstab the fix won't effect that drive. You'll have to edit fstab to add "usefree" to it somehow. 
(read the last two comments, it will explain why this may not be fixed for you.)

---

### Post by Liet on 2007-11-09
thanks, it works :)

---

