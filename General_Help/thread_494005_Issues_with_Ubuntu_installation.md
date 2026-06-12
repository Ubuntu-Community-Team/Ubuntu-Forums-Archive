---
title: "Issues with Ubuntu installation"
date: 2007-07-06
forum: General Help
---

### Post by pandaeater123 on 2007-07-06
this is my first post, so im not sure if im in the right forum to ask it, but this seems right..

anyway, I'm getting this "kernel panic" thing that says something about IO=APIC and to boot with noapic. I searched my problem and typed in "noapci noapic" which got it booting. Then something strange happened. instead of installing, it went into a non-GUI form of ubuntu, saying something about the X (which im going to guess is the name for the GUI) wasn't working and threw me into a DOS like setting. 
 i have burned at least 5 different cds/dvds to try to get it too work.

dunno if this helps, but heres my rig (im not trying to brag..)

amd 5600+
8800GTS
3 gigs of RAM
foxconn 590 sli mobo
thermaltake 700watt psu

and a couple other things in there that shouldn't mess up installation. (agiea physx card i got for free from a RICH freind who didn't like it, and a wireless card.)

Help? Don't wanna use windows xp anymore...

---

### Post by loserboy on 2007-07-06
I know the 8800s are giving people problems, try searching for workarounds, i think that's what the problem is on top of the apic problem

---

### Post by southernman on 2007-07-06
Try this:

> sudo dpkg-reconfigure xserver-xorg

Enter the above command and follow the onscreen instructions to the best of your knowledge

---

### Post by MCSE_Crossover on 2007-07-06
what kind of motherboard do you have?

I would also try booting with the "irqpoll" statement in your boot string

---

### Post by pandaeater123 on 2007-07-06
> **MCSE_Crossover said:**
> what kind of motherboard do you have?

I would also try booting with the "irqpoll" statement in your boot string

foxconn 590 sli mobo

---

