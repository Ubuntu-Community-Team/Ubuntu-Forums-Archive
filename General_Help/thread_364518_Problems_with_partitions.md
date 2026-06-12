---
title: "Problems with partitions"
date: 2007-02-18
forum: General Help
---

### Post by saximus on 2007-02-18
Hello,

I've installed Ubuntu and i'm trying to get used to it at the moment. I have one problem though. I didn't allocate enough space on the ubuntu and xp boot partitions, and I have loads of space left over. I have tried several different free partition resize and management programs, but none of them seems to be able to allocate free space to my primary partition - which is exactly what I'm trying to do.. The only program that has been able to do this that I have seen so far is partition magic - which is expensive. Does anyone know of any partitioning programs that are able to increase the size of the primary disk in ntfs format and the boot disk of ubuntu without destroying the data on the partitions? I really hope someone has a solution.

---

### Post by solar george on 2007-02-18
[Gparted]("http://gparted.sourceforge.net/features.php") or parted

I think gparted is on the live cd.

If not you could install it on your ubuntu system

---

### Post by taurus on 2007-02-18
Maybe this one!

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by Orfeus on 2007-02-18
or there is an easier way by using partition magic on windows Xp

---

### Post by saximus on 2007-02-18
Hey - thanks for the tips

I've tried using Gparted, but it does not seem to be able to allocate free space to my boot partitions.. It is able to edit my extended partitions, but not the boot partition. 

I also tried to download the demo of partition magic for xp, and that would have worked if it wasn't for limitations on the demo.. 

[Edit] Deleting the last sentence for illegal activity...

---

### Post by saximus on 2007-02-18
sorry - I was not aware that I was not allowed to talk about that in this forum - I will not do that again. 

Anyways - partition magic seems to be the most promising program.

---

### Post by solar george on 2007-02-18
> It is able to edit my extended partitions, but not the boot partition. 

Sounds like the free space is in a extended area of the drive and the boot is in the primary.
[http://tldp.org/HOWTO/Partition/partition-types.html]("http://tldp.org/HOWTO/Partition/partition-types.html")
Read sections 3.3 & 3.4 - these may explain if you don't know what I mean. If you do then disregard the explanation.

---

### Post by saximus on 2007-02-18
Thanks! 

That makes sense, and it clears things up - it explains my problem at least:) 

Is there any way to make my computer get rid of or disregard this distinction?

---

