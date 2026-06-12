---
title: "how I can make Windows XP bootable?"
date: 2008-03-17
forum: General Help
---

### Post by lonely man on 2008-03-17
hi all

I have Windows Vista and Ubuntu on my PC, and I was plane to install windows XP beside them, I install the stupid XP and after instillation  the boot for Windows Vista and Ubuntu has removed and I can only use Windows XP, when I saw that I tried to fix it by the stupid Windows Vista DVD, I lunch the start-up dvd and I made repair  for the boot, but what I get after that that I can only use windows vista, I thought windows Vista will fix the problem and it well make dual boot for XP and Vista, after that I said I will install Ubuntu and after that I'll see what I can do.

now I can run Vista and Ubuntu only, I have XP, but I can't boot it up.
I need ur help guys to solve this problem to make windows XP boot

and thanxs in advance

---

### Post by billgoldberg on 2008-03-17
The super grub disk (live cd) will allow you to boot each operating system.

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

I used it last week, I added xp to a 30gb partition and it overwrote the grub. With supergrub I could boot the partion.

You can then add the windows partition that won't boot to the grub.

I folowed the steps displayed [here]("http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/") to do that.

---

### Post by tbrminsanity on 2008-03-17
I think the official way of setting up the three is to install XP first, then Vista and mark it as a dual boot (Vista/XP) Install.  Then install Ubuntu which will encapsulate the other two.  You may have to choose first to load Vista from GRUB then select XP folliwing that to get into XP but that should work.

Out of curiosity, why do you need all three anyway?  Besides problems with drivers Vista can do prety much everything XP can.  Since you have Vista you might as well have a Vista/Ubutnu machine.

---

### Post by lonely man on 2008-03-17
> **tbrminsanity said:**
> I think the official way of setting up the three is to install XP first, then Vista and mark it as a dual boot (Vista/XP) Install.  Then install Ubuntu which will encapsulate the other two.  You may have to choose first to load Vista from GRUB then select XP folliwing that to get into XP but that should work.

Out of curiosity, why do you need all three anyway?  Besides problems with drivers Vista can do prety much everything XP can.  Since you have Vista you might as well have a Vista/Ubutnu machine.

hi..

this what I plane to do...

but whay to install 3 OSs, ubuntu it's for master use, XP for gameplay use, Vista Cuz I have it origina and for some resonl :lolflag:

---

### Post by sandysandy on 2008-03-17
have a look at these links

[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

[http://apcmag.com/node/5162/](http://apcmag.com/node/5162/)

[http://ubuntuforums.org/showthread.php?t=220452](http://ubuntuforums.org/showthread.php?t=220452)

[http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php](http://lifehacker.com/software/ubuntu/hack-attack-how-to-tripleboot-windows-xp-vista-and-ubuntu-193474.php)

regards

---

