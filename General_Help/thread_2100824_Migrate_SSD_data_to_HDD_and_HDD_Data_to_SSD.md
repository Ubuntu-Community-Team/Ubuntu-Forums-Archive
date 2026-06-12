---
title: "Migrate SSD data to HDD and HDD Data to SSD"
date: 2013-01-02
forum: General Help
---

### Post by Newku on 2013-01-02
So, I just installed Xubuntu 12.10 on my computer and made an embarrassingly stupid mistake.

I have a 128 gb SSD in my computer and a 500 gb HDD. The SSD is supposed to contain Xubuntu's / directory while the HDD is partitioned half for Windows and half for /home. When I was installing however I got these confused so that my /home directory is on the SSD and my / directory is on the HDD. Is there any simple way I can fix this without reinstalling and losing all my precious configurations and stuff I spent hours on?

---

### Post by oldfred on 2013-01-03
How much room do you have on HDD or can make room by shrinking or removing / (root).

I would copy /home to the hard drive and reinstall Ubuntu to SSD but with manual install you can choose to reuse /home from the hard drive, just DO NOT format it during install. You have to use Something Else or manual install to have that option.

Move is similar to this:
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)


If only having Ubuntu on SSD you may want to consider gpt partitioning. Arch recommends it for SSD and it is required for drives over 2TB. But you can only use gpt with Windows boot drive if using UEFI.
       
 [https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)


I now leave /home inside my / (root) but split /home into the user configuration files which are mostly hidden and data. Then I have all data on my hard drive and / with /home on SSD. That way the SSD is fully bootable even if hard drive fails. Of course if drive failed my data would not mount, but hopefully I have backed all that up recently.
       
 Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

