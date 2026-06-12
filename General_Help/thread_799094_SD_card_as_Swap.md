---
title: "SD card as Swap ?"
date: 2008-05-18
forum: General Help
---

### Post by hooksie on 2008-05-18
Is there anyway I can turn my SD card into swap space ?

My current implementation is Ubuntu installed to a 4gig flash drive, but I didnt partition it with any swap space (2 gigs of physical memory, figured I wouldn't need it.  Mistake ?)  I don't want to touch my hard drive, but I have an SD card that's always in and has plenty of space.

---

### Post by tamoneya on 2008-05-18
that should be fine.  Partition the sd card as a swap partition like you would normally and then add it to /etc/fstab as a swap partition.  You should make sure that in fstab you identify the card by its UUID as its device node may change.

---

### Post by kerry_s on 2008-05-18
2 gigs of ram you don't need it. if you want to cover your bases you can install swapd, it creates a swap file when more memory is needed and removes it when no longer needed, it's called dynamic swap.

**sudo apt-get install swapd**

---

### Post by Tomatz on 2008-05-18
2gb of ram is more than enough physical ram.


Swapping flash memory is better than using HDD swap because of the low seek time but sd cards are pretty sluggish so you may as well stick with a standard swap partition or page file (the latter you can easily impliment after install) ;)

---

### Post by hooksie on 2008-05-18
In all reality actually creating swap space isnt so much a big deal to me if the 2 gigs of Physical Ram is enough.  The main reason I was going to try this is because GDM wont actually load past login, it just seems to hang.  (Thought maybe some swap would help out).

---

