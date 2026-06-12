---
title: "just installed 6.10"
date: 2006-12-22
forum: General Help
---

### Post by war-totem on 2006-12-22
and was confused by the whole partitioning not being used to it.  So I mistakenly allocated 130 gb to linux leaving only a tiny bit to my windows partition.  My question is, is there a way to reallocate some of that back to windows from linux?

---

### Post by hanzomon4 on 2006-12-22
Yes, install gparted ```
sudo apt-get install gparted
``` It's a gui partitioning tool.... I'll play around to see if I can give you exact instructions

---

### Post by logos34 on 2006-12-22
To resize your partitions they cannot be mounted, so just reboot to the livecd, choose run/install and let it load the desktop, and go to Administration>gnome partition editor, choose a partition and click on "resize/move".  Drag the slider to shrink the linux ext3 and then enlarge the windows/ntfs partition into the free space.  But if your swap file is between the two (like mine) this won't work.

---

### Post by viper on 2006-12-22
You might want to download the Gparted live cd.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Azakus on 2006-12-23
Remember this well. **Make only one change to a partition at a time (that is to say, shrink in one action, press the "Make Changes" button, then do the addition to the Windows Partition)**. That is the safest way to go about it, and the time I tried to do it all at once it failed horribly. Also, **make a backup**.

---

