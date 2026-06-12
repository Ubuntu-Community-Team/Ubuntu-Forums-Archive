---
title: "Help with RAID"
date: 2007-02-17
forum: General Help
---

### Post by aivegas on 2007-02-17
I am new to all of this, but I am running Kubuntu 6.10 on the following system:
Asus A8V-VM
Athlon 64 3200+
2x512MB DDR400
ATI Radeon X1900GT
20GB HDD (System Drive)
4x320GB WD HDD's

I am confused when it comes to how to run the HDD's in RAID5.  Do I need to create a RAID set through BIOS options like back when I was running Windows?  Do I simply download a program and do everything from within Linux?  If possible I would prefer to run everything with software RAID so that if my motherboard dies after it is out of warranty I don't have to track down another one of these.  Also, if doing software RAID, do I need to set the drives to IDE or RAID mode in the BIOS?
TIA
Corey

---

### Post by MeepZero on 2007-02-17
this is exactly the same problem I am having now.  My motherboard does not have any hardware raid options, so I need to find a way to enable software raid in edgy.  If anyone knows where I can start with this I would love to hear it!

---

### Post by nyinge on 2007-02-18
Here are the 2 helpful pages:
[FakeRaidHowTo]("https://help.ubuntu.com/community/FakeRaidHowto")
[FakeRaidEdgy]("https://wiki.ubuntu.com/FakeRaidEdgy")

It takes a lot of reading and patience, but you'll eventually get it.  :)  I've tried it once on RAID 0 and succeeded, but I really wish that Ubuntu's installer could take care of those problems just as easily as Fedora's Anaconda could.

---

