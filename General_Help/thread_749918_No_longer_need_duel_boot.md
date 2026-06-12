---
title: "No longer need duel boot"
date: 2008-04-08
forum: General Help
---

### Post by Beastboy26 on 2008-04-08
I am (soon to be was) duel booting my laptop with that other o/s, now I am ready to just get rid of it all together...  I just don't want to loose my settings and customization that I already have in Ubuntu.  So what is the best way to get rid of the other o/s, give the disk space to Ubuntu, and loose the grub menu?  Any good how to websites?

---

### Post by climatewarrior on 2008-04-08
You can get a live cd called gparted(Which is free as in beer and freedom). With that live cd you will be able to erase the partition where your other os is and expand your ubuntu partition. All of this is in a graphical environment so its not hard to figure it out. But if you like there are many tutorials available online. Although you should be very careful with which partition you erase. As for the menu that's quite easy too. The menu is called grub and there are various graphical tools available to modify that. One example is Grubconf. Also changing the configuration manually its quite easy too if you don't mind working with a text file.

---

### Post by ibutho on 2008-04-08
I don't know of any howto sites, but hopefully I can give you an idea of what you need to do. If you no longer require the Windows partition, you can format it to ext3 from within Ubuntu using gparted or mkfs.ext3 (unmount the partition first before doing any operations on it). After that you need to create and entry for your new ext3 partition in /etc/fstab and create a mount point for it in /media. once thats done you can then mount your partition and use it. You can edit /boot/grub/menu.lst and get rid of the Windows entry.

---

