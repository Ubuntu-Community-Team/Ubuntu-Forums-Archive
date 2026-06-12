---
title: "How mount disk partitions in Xubuntu 16.04"
date: 2016-09-27
forum: General Help
---

### Post by Ralph L on 2016-09-27
I am (hopefully) in the process of switch from xubuntu 14.04 to xubuntu 16,04.  I have a number of partitions on my hard disk, which I don't want always mounted, but which I can mount when needed.  Under thunar (14.04) all the partitions show up in the side panel and I can easily mount and unmount them.  In thunar 16.04 these partitions are not listed in the side panel.  How do I get them listed so I can easily mount and dismount them?  It seems like somebody took a very valuable capability out of thunar 16.04.

---

### Post by &amp;KyT$0P# on 2016-09-27
What do these partitions show up like in GParted?

If you don't have GParted, install it with this command in the Terminal -
```
sudo apt-get install gparted
```

---

### Post by Ralph L on 2016-09-27
The partitions show up in gparted just like any other partition.  They can moved and resized like always.  The only thing is gparted won't mount them--or at least I couldn't find a way to get gparted to mount them.  I thought about installing nemo, but it drags in a lot of the cinnamon desktop, and I would like to keep my new 16.04 partition as small as possible.  I did install gnome-disk-utility, but even the new version of that no longer shows all the partitions.  It wouldn't show any of the sub-partitions in the extended partition.

---

### Post by &amp;KyT$0P# on 2016-09-27
Wait, are these all logical partitions (meaning, not primary partitions)?

---

### Post by Ralph L on 2016-09-27
I restarted the installation from scratch.  Downloaded xubuntu 16.04.1, reinstalled it and it fixed this and another problem.  Don't know what was wrong, but thunar now shows all my partitions.  Thanks to those that responded.

---

