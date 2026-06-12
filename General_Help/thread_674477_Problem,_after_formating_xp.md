---
title: "Problem, after formating xp"
date: 2008-01-21
forum: General Help
---

### Post by Ibrahim mufeed on 2008-01-21
Hi, I am a Newbie and this is my first post...

I have installed Ubuntu 7.10 on my desktop with partition magic help, now my computer running two OSs; Ubuntu and XP.

Then I need to format the XP, when I finished formating and reinstalling xp again, a new problem appear, that is my computer did not see the Ubuntu OS.

I need help, how to go to Ubuntu???

---

### Post by apjone on 2008-01-21
> **Ibrahim mufeed said:**
> Hi, I am a Newbie and this is my first post...

I have installed Ubuntu 7.10 on my desktop with partition magic help, now my computer running two OSs; Ubuntu and XP.

Then I need to format the XP, when I finished formating and reinstalling xp again, a new problem appear, that is my computer did not see the Ubuntu OS.

I need help, how to go to Ubuntu???



Windows Boot loader has over wrote the boot record. You need to either manually add it in or install GRUB

---

### Post by Ibrahim mufeed on 2008-01-21
How to do that, I really did not know...

---

### Post by Craigus on 2008-01-21
The easy way:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by DJ_Peng on 2008-01-21
Welcome to Ubuntu! For future reference, it's always good to install Windows first, then install your Linux. Linux plays well with an existing Windows install, but Windows definitely doesn't play as nicely with other operating systems.

---

### Post by Ibrahim mufeed on 2008-01-21
I really do not know how or even what it is...
I need instructions 1..2 steps. the simpleset way..Please.
So sorry.

---

### Post by Craigus on 2008-01-21
> I reinstalled Windows and Linux no longer boots.

   1. boot your SGD floppy disk, USB disk or CD-ROM
   2. English Super Grub Disk
   3. Gnu/Linux
   4. Fix Boot of Gnu/Linux (GRUB)
   5. select your Linux partition
   6. see message, 'SGD has succeeded'
   7. you're done! reboot

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Boot_Master_Boot_Record]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Boot_Master_Boot_Record")

---

