---
title: "Uninstalled Ubuntu 7.04 with the fixmbr command...."
date: 2007-06-04
forum: General Help
---

### Post by BCHurricane89 on 2007-06-04
but uh, how do i get my partition back, so that I can have the space back for my windows partition. In other words, I want to repartition the hard drive space that I used for ubuntu, and put it back to the win xp partition. GRUB boot thing is gone, just need help with the left over partition space..merging! thanks!:D

---

### Post by zvacet on 2007-06-04
[http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php")

---

### Post by BCHurricane89 on 2007-06-05
Ok thanks, ill try doing that...hope I can figure it out thanks! Maybe ill just use a LiveCD for Ubuntu when I do use it.

---

### Post by Bohlio on 2007-06-05
Just so I can get this clear...
 fixmbr is a command you can type in the windows command line... and it gets rid of grub? or does it just bypass it and go around grub straight to windows.

---

### Post by zvacet on 2007-06-05
It is easy to use and have more options then Live Cd.that is the reason I recomended it to you.

---

### Post by orb9220 on 2007-06-05
> fixmbr is a command you can type in the windows command line... and it gets rid of grub?

Is On the winXP Cd to fix the mbr (MasterBootRecord) which is a small bit at the beginning of the Hard Drive.  Which once run wipes out the grub only the Linux partitions are still there.

---

### Post by BCHurricane89 on 2007-06-05
Yes, I got the linux partitions...well, I see them and they were ext3, so I converted them to ntfs, now how to I merge them into my existing win xp partition?

---

### Post by merlinus on 2007-06-05
gparted live cd from [http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

