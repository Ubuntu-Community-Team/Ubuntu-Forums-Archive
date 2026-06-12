---
title: "Ubuntu running slugish"
date: 2007-03-16
forum: General Help
---

### Post by Moe70 on 2007-03-16
Everything is a bit slow i think its because of graphics. the resolution doesnt change, i think the graphics card needs drivers or something. Ive got an ATI X1300. Ive ran the cd but it appears to be a windows only cd...is there linux drivers for it... does it even need a driver on linux?

Also can someone tell me how to see how much cpu/ran is taken (like on windows ctrl alt del) to see if its actually taking alot of memory or its the graphics card thats making it look slow

---

### Post by annda on 2007-03-16
you can see what is running and what resources it uses here:
system > administration > system monitor (click the processes tab)
or type top in the terminal.

a driver can be a good thing. there are three linux drivers for ati at the moment: ati, radeon (included in ubuntu) and fglrx (available in repositories through restricted kernel modules). search the forums and google around for your card to see which supports your card. i used to have an ati card (on a laptop) and the radeon driver was MUCH faster than the default ati.

---

### Post by Moe70 on 2007-03-16
thanks.ive installed the x1300 driver or wateva it was (codes in terminal) its working now :)

---

