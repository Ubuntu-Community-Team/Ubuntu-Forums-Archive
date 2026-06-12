---
title: "Error 18 in GRUB"
date: 2006-10-15
forum: General Help
---

### Post by max.diems on 2006-10-15
I have a system that has been working perfectly well for several monts. When I tried to boot this morning, I got an error 18 in GRUB. I've heard taht this can be caused be caused by bad partitioning, but it has been working, so I'm not sure what's going on.

---

### Post by catlett on 2006-10-15
Has anything changed at all? Did you partition anything or change your bios? I only ask because this is the meaning of error 18 (at least from the gentoo grub wiki but gentoo's wikis are always good sources of information)
> Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). 

---

### Post by Kateikyoushi on 2006-10-15
Did you run an update before the last shutdown ?

---

### Post by max.diems on 2006-10-15
BIOS: Not changed until after getting problem (trying to make it boot from CD)
Updates: None recent

---

### Post by catlett on 2006-10-15
Try reinstalling grub from the live cd. It can't hurt and may even help. Just boot to a live cd or use ubuntu's live install cd. Open a terminal and get to a grub shell with ```
sudo grub
``` I listed the commands in a small how to, [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)
It's worth a shot. If you get a new error, post.

---

### Post by jkvv_1973 on 2006-10-16
google

"super grub disc"

its an iso image file you have to burn to cd...

then boot via this cdrom...it fixed my grub (error 22) 

and it does it instantly...

---

### Post by max.diems on 2006-10-27
> **jkvv_1973 said:**
>  
its an iso image file you have to burn to cd...
Kills it for me-- dialup sucks:(.

---

### Post by Bigbluecat on 2006-10-27
It's a very small ISO file and extremely useful to keep around. Highly recommended.

---

### Post by max.diems on 2006-10-27
Wow, that is small. I'm getting ready to try it.

---

### Post by max.diems on 2006-10-28
SGD hasn't worked so far, catlett's HOWTO hasn't helped (though good advice for others, just not working here). I'm trying to use grub-install, warn me if this'll foul up the system. I'm using a 5.10 live CD, system is 6,06, coud that be it? grub-install is taking longer than it seems it should (around four hors of probing so far). Maybe something I need to do specifically in SGD? All of my files are still there, I can get them from the 5.10 live system.

---

### Post by max.diems on 2006-10-28
*bump*

---

### Post by Herman on 2006-10-28
Just try reducing the size of your Ubuntu partition a little bit. Or even a lot, and then resize it bigger a little at a time as much as you can get away with. 
Nothing guaranteed, but it has worked for error 18 a few times. It depends on what kind of BIOS you have.
 
Regards, Herman :D

---

### Post by max.diems on 2006-10-29
How do I resize w/o losing everything?

---

### Post by Herman on 2006-10-29
You should make backups of everything before you resize or do anything with any disk partitioning software.
Well, actually, you should always have at least your most important files backed up somewhere else at all times anyway. A hard disk can fail by itself, you never know, it's not too common, but it can happen.

I use and recommend [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") , that is free and only 30 mb and has [ Partimage]("http://www.partimage.org/Main_Page") in it as well, if you want to back up your entitre partition. You would need some other media that's large enough, such as another hard disk or a USB drive.
[GParted -- LiveCD ]("http://gparted.sourceforge.net/livecd.php")is the easiest and best way to resize partitions for Ubuntu in my opinion. I have been using it for a long time and it just keeps getting better and better. :D

Regards, Herman :D

---

### Post by max.diems on 2006-10-29
[quote=Herman;1684126
only 30 mb [/quote]

ONLY?!?!?! When the FF download takes almost an hour, 30mb is not only. :cry:

---

### Post by Herman on 2006-10-30
[QUOTE]max.diems 	> **Herman said:**
> 

ONLY?!?!?! When the FF download takes almost an hour, 30mb is not only. :cry:  Sorry max.diems, I forgot. Maybe try using GParted in the 'Desktop' Live CD then?
Did you install Ubuntu with the 'Desktop' Live CD?
Regards, Herman :D

---

### Post by max.diems on 2006-11-07
It switched to error 2 now :/
Does using the 5.10 liveCD have anything to do with that?

---

