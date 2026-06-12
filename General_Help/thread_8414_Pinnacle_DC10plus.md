---
title: "Pinnacle DC10plus"
date: 2004-12-17
forum: General Help
---

### Post by gazza on 2004-12-17
Anyone know how to get this card up and running.  It is a zoran 36057 and I have downloaded drivers from site by  Laurent Pinchart and Ronald Bultje.

They say I should not need them as driver is in 2.6 kernel but modprobe says no, and their make, makefile instructions don't seem to work.

 :cry: I am a newbie ofcourse

Gazza

---

### Post by Averatec5400 on 2004-12-20
[QUOTE=gazza]Anyone know how to get this card up and running.  It is a zoran 36057 and I have downloaded drivers from site by  Laurent Pinchart and Ronald Bultje.

They say I should not need them as driver is in 2.6 kernel but modprobe says no, and their make, makefile instructions don't seem to work.

 :cry: I am a newbie ofcourse

Gazza[/QUOTE]
 I have one of those cards, pinnacle hardly supported it on anything above 98, I amnot sure the linux drivers ever got to a mature state that I saw, I have been following it for years and never got anything good out of any driver for it beyond windows 98 FIRSt edition.

---

### Post by fsman on 2005-02-04
this working fine for me in Mandrake 10.1
All I had to do was to add the following line to modules.conf
alias char-major-81-0 zr36067

I suspect that the mandrake kernel has been compiled with the zoran driver included hence it works out of the box.

I think that for ubuntu and kernel rebuild is required with a make menuconfig to turn on the zoran driver in the kernel. (That said, I'm a little new to Linux so I could be wrong)

---

