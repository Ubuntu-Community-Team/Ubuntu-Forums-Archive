---
title: "During instalation, won't partition..."
date: 2007-02-09
forum: General Help
---

### Post by Hob Hayward on 2007-02-09
Hey, I'm trying to install ubuntu 6.10 on a friend's laptop, but when I go to partition, either with the installer's partition manager, or with gparted. Anyone have any ideas why this would be not working.

Hes got a toshiba tablet PC if it matters.

Thanks!

---

### Post by Bartender on 2007-02-09
More details, please - what do you mean it won't partition?  What are you trying to do, and what happens when you do it?

You mention gparted.  Do you have a GParted LiveCD?

---

### Post by Hob Hayward on 2007-02-09
Sorry for not being clearer.

What happens is I start the partitioning, using the gparted that comes with the ubuntu live cd. It acts like something is happening with the spinning mouse wheel and such, but it just keeps doing that, and when I left it, it did it for over an hour, so clearly something is not working right.

I do not have a gparted livecd.

---

### Post by Bartender on 2007-02-09
Do you have access to broadband on another PC?  Try building a CD from the latest download at this [site]("http://gparted.sourceforge.net/livecd.php").  Same process as making an Ubuntu CD.  Download the latest version, burn it to a CD so that the ISO becomes a bootable CD.
This is an awesome partitioning tool.  You boot from the CD, follow the prompts, you'll see a map of the partitions that will look just like the one you saw from the LiveCD.

People seem to get more reliable results from the stand-alone GPLCD than from the Ubuntu CD.

---

### Post by Hob Hayward on 2007-02-09
Well, x failed to star with the gparted disc.

It looks now like the partitioning was working in the first place, just VERY slowly. According to explorer in windows, the disc has been partitioned, but according to gparted and partition magic, the main hard drive has now become 55 gb, while I know its only 28gb.

My only question now, is now, if I use partition magic to decrease the partition size to 32gb, what will be erased form the hd to do that? Will it be the part of the HD that actually doesn't have anything, or will it be random parts that could include the files which I need on the windows xp partition?


Edit: Well, I just tried resizing with partition magic, after it recognized the actually 28 gigs present, but it gave me an error saying that there wasa directory mismatch or somesuch.

---

