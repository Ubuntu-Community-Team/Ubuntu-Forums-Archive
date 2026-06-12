---
title: "how to erase Ubuntu and go back to XP when dual boot"
date: 2007-10-11
forum: General Help
---

### Post by juantastico on 2007-10-11
I have dual boot Ubuntu and  XP, but now i want to erase Ubuntu and only use XP with out having to reinstall XP is there  an esay way to do this. . Do not get me wrong i love Ubuntu but due to work and school and need to go back to XP (please do not ask why). I will try ubuntu for sure in a near future.

thanks for all your assistance 
:guitar:

This is the tutorial i used for the dual boot
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty)

thanks

---

### Post by cessna_89702 on 2007-10-11
I think you can use "Super Grub" by installing from here [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Then delete ubuntus partitions and restore the windows mbr...........

OR you could erase grub with the windows mbr and have it go to windows and delete the ubuntu partitions from there...




**You can install from another spot but thats the first one that came up for me

---

### Post by artesvida on 2007-10-11
I'm not sure I understand your problem.  If you're dual-booting, can't you use XP already?  One of my PCs is dual boot and (please don't flame me!) I haven't booted it to Ubuntu in many many months.  Do you need to reclaim the disk space?  Remember, you can't incorporate the Linux disk space with the existing Windows disk, at least not without GPartEd or something.

I believe you will need to:
1.  Blow away the linux and linux swap partitions.
2.  Repair the Windows install, because I believe that Ubuntu got rid of the Windows bootloader and replaced it with GRUB.  <<NOTE:  I may be wrong on this point, but I don't see how repairing the Windows install will hurt.>>

I hope someone else chimes in on this, because I haven't actually gone through these steps.  But, I think that will get rid of Ubuntu.

Good luck!

---

### Post by jocko on 2007-10-11
You'll probably need to boot from a Windows install cd, and use it to repair the boot sector (don't know exactly how it's done, but the installer should have a repair option).
Once you have repaired the boot sector and verified that windows boots without going through grub you can delete and re-format the ubuntu partition:(.

---

### Post by juantastico on 2007-10-11
will this erase my XP files and settings? or will they remain intact

thanks for your help so far

---

### Post by drFUNK on 2007-10-11
> **jocko said:**
> You'll probably need to boot from a Windows install cd, and use it to repair the boot sector (don't know exactly how it's done, but the installer should have a repair option).
You have to recover the MBR.  You boot the windows XP CD and select "recovery console."  You then type the command fixmbr and choose your XP install.  This will remove grub and let you boot directly into windows.  You can remove the ubuntu partition through disk management.  This can be found by right clicking "My Computer" and click manage.

---

### Post by junknstuff on 2007-10-11
good info! was thinking about doing this to my laptop and just running ubuntu on the desktop or something along those lines

---

### Post by juantastico on 2007-10-12
I will try these instructions:) later and post my findings

---

