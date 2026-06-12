---
title: "Moving from XP to Ubuntu"
date: 2007-09-13
forum: General Help
---

### Post by NoSkill on 2007-09-13
Hi,

          I have decided to move from XP to unbuntu but I first have some questions I would like answered before I start moving.

          Firstly, I want to dual boot XP and ubuntu since I have some XP only programs which I work with regularly. Here comes the tricky part, however, on XP I have 4 Hardrives Seagate Baraccuda 7200.10 320GB arranged in Raid 10. Now, most of the space provided by these harddrives is already occupied. The controller I used for the RAID was provided by Intel and installed during the installation of windows XP.

How do I make the transition to ubuntu? Will the installer recognize the RAID of my harddrives? Will I have to reinstall XP in order to dual boot?

The only way i can think of actually doing this is to yank out 2 of my hardrives since they are in raid 10. Format them and put them back in, afterwards I should be able to install Ubuntu on them and dual boot.
Would this work? what other choices do i have?

Thank you

---

### Post by trippinnik on 2007-09-13
What are the applications?  If they're games, then yeah you'll still have to dual boot, but most anything else can be run under linux using Virtualization.

---

### Post by Amazona aestiva on 2007-09-13
See [this]("http://wubi-installer.org/") page.
You might try it, but make backups!

---

### Post by NoSkill on 2007-09-13
the applications that I run would include Unigraphics NX3, autocad, Metrowerks CodeWarrior, and visual studio.

I dont really play games. Would the above applications work under wine?

---

### Post by Maestro23 on 2007-09-13
> **NoSkill said:**
> the applications that I run would include Unigraphics NX3, autocad, Metrowerks CodeWarrior, and visual studio.

I dont really play games. Would the above applications work under wine?

To see if those apps will work under WINE, go check the Wine App Database: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by trippinnik on 2007-09-14
You'll definetly be able to run them in a VM like Virtual Box, also since a few of them are IDEs you might try some of the linux native IDEs or Eclipse (runs on java but plugins for everything), K Develop, Mono develop and Anjunta.

---

