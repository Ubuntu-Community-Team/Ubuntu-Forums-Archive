---
title: "Need Help Uninstalling Ubuntu"
date: 2008-04-22
forum: General Help
---

### Post by Jenga-kun on 2008-04-22
Hi my laptop originally had windows vista on it but I hate windows (especially vista) so I dual booted ubuntu onto it. Now I'm selling my laptop and I need to uninstall ubuntu and put the partitions back together. Can somebody help me?

---

### Post by skymera on 2008-04-22
Well format the parititon in Windows then resize them. Easy.

A good program is ParititonMagic.

---

### Post by Wandering on 2008-04-22
All the software you need is in Vista.

Click on the orb, and right click on Computer

Click on manage

When the window opens, click on disk manager

Select the partition(s) you want to get rid of and remove it.

Resize the remaining partition. 

Have fun!

---

### Post by Jenga-kun on 2008-04-23
Thanks for the hlep but I'm still stuck with the grub loader so now I can't even boot windows.

---

### Post by forestpixie on 2008-04-23
I assume that you deleted all the buntu partitions before you fixed the mbr. You need to run fixmbr - if you have the vista disc boot with that and you should be able to fixmbr which is what you need to do. If you don't you can use supergrub to fix the mbr - you'll need to be able to get to a pc and download it, then burn it as an image not as a data disc and then you can bott with that to fix it.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Helios38 on 2008-04-23
you need to restore the Windows boot loader.


[http://ubuntuforums.org/showthread.php?p=3257028](http://ubuntuforums.org/showthread.php?p=3257028)

---

