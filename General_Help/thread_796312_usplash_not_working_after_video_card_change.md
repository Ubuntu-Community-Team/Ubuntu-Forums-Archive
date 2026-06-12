---
title: "usplash not working after video card change"
date: 2008-05-16
forum: General Help
---

### Post by dwasifar on 2008-05-16
I switched from an ATI card to an Nvidia card.  I successfully installed the Nvidia binary driver, and the system works fine, except that usplash doesn't work any more and nothing I try gets it to work.  

After the POST screen, the monitor displays "No Signal Detected" and goes into standby for about as much time as the usplash should take; it wakes up again when the Nvidia splash appears, and from there it boots normally.

I have tried the advice in [this thread]("http://ubuntuforums.org/showthread.php?p=4356890") for every resolution the monitor supports up to 1680x1050.  I have also tried using startupmanager to accomplish the same thing.  I've reinstalled usplash from Synaptic too.  Nothing has helped.

I know it CAN work with this card, because I get the splash when I boot from a live CD.

Right now as a workaround I have the splash disabled in grub menu.lst.  But I would like the splash back.  Anyone?

---

### Post by wpshooter on 2008-05-16
Seems to me that there is some type of Usplash configuration/resolution file that can be edited to set this resolution to the proper setting.  I don't recall the exact name right now.  Maybe someone else can name it for you or perhaps a few search on "usplash resolution" may find it for you.

Good luck.

---

### Post by dwasifar on 2008-05-16
> **wpshooter said:**
> Seems to me that there is some type of Usplash configuration/resolution file that can be edited to set this resolution to the proper setting.  I don't recall the exact name right now.  Maybe someone else can name it for you or perhaps a few search on "usplash resolution" may find it for you.

Good luck.

You're thinking of /etc/usplash.conf, right?  I wish it were that simple.  :(

---

### Post by dwasifar on 2008-05-18
bump

---

### Post by dwasifar on 2008-05-26
one last bump

---

