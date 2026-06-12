---
title: "Hard Drive Help"
date: 2008-02-17
forum: General Help
---

### Post by GeoffVanstone on 2008-02-17
Hi,
 I'm new to Ubuntu, I've seen in action before and I am now getting it and getting rid of Windows Vista. I was wondering if any of yall know of a program I can use to format or wipe my Hard Drive Partition that works with ubuntu. I am installing ubuntu on a partition, and will be erasing the other hopefully when I am on Ubuntu. I just dont know a program to use.

So could someone please help me. Thanks for any Help. And if you need me to furture explain, as I may not be clear (LOL), then just ask me and I'll try my best.

Thanks Again.

-Geoff

---

### Post by Sokertes on 2008-02-17
I have used gparted a couple of times just to do what you want. You can get it at 

[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

It is a live cd that you boot your computer with to repartition, shrink, grow partitions on harddrives. It works like a charm.


Sokertes

---

### Post by GeoffVanstone on 2008-02-17
> **Sokertes said:**
> I have used gparted a couple of times just to do what you want. You can get it at 

[http://gparted.sourceforge.net/download.php]("http://gparted.sourceforge.net/download.php")

It is a live cd that you boot your computer with to repartition, shrink, grow partitions on harddrives. It works like a charm.


Sokertes


So GParted will reformat, or erase a partition? and I run that CD from Boot?

---

### Post by Sokertes on 2008-02-17
You can do that and then some. It is basically like fdisk with a GUI.

It can Detect, Read, Create, Grow, Shrink, Move, Copy, Check partitions of your hard drive and do this all on a bootable cd. I have used it to do just what you want to do, nuke my windows partition.

Basically what I did was nuke the windows partition, then grow (make bigger) my / partition. Then create another reiserfs partition for my development storage area.

I have it in my very valuable personal tool box (cd holder) for working on PC's and servers.

---

### Post by sammydee on 2008-02-17
No need to download the gparted live cd - the ubuntu live cd comes with gparted!

You can even partition your disks during the install process.

---

### Post by uberlube on 2008-02-17
Although if you do want a live CD to hold onto for all your partitioning needs grab the new version of Parted Magic

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

Its the best ! :)

---

### Post by seventhc on 2008-02-17
If your getting rid of windows and installing Ubuntu only, then during install leave all the defaults and it will wipe windows and create/format the needed partitions. This option erases windows so that only Ubuntu will boot.

---

### Post by GeoffVanstone on 2008-02-18
I Just ended up using:

[http://dban.sourceforge.net](http://dban.sourceforge.net)

It did a good job wiping my hard disk, then I ran the Ubuntu CD from boot, and installed it. It all worked out, and thank you all for all your assistance.

-Geoff

---

