---
title: "How can I transfer grub menu to windows disk"
date: 2017-09-06
forum: General Help
---

### Post by fftorettol on 2017-09-06
I have currently installed Win10 and Ubuntu on my PC. I am using both OS for more than a year. But once, sleep and hibernation stop working on Windows and few days ago, I decided to fix that. I tried many things (from restoring Windows, clean boot etc..) I have 2 disk in my PC. One is SSD (where I keep my Windows OS installed) and the second one is HDD. On HDD, i've have a partition where I keep Linux. 
The problem is that in order to have an abillity to boot into Linux, I have to select the second disk (HDD) to boot first. But if I boot into bios and select that SSD boots first, I have no longer issues with sleep and hibernation. But then I can't see the grub menu and can't boot into linux. So is there anyway that I transfer only the grub menu on SSD, so that SDD can load first and still shows grub menu? What else do you suggest me guys?


Thanks community!

---

### Post by oldfred on 2017-09-06
UEFI or BIOS?

       May be best to see details, you can run from your Ubuntu live installer or any working install, use ppa version not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by fftorettol on 2017-09-06
You are right.. Its UEFI not BIOS

---

