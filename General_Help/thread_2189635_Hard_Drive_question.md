---
title: "Hard Drive question"
date: 2013-11-23
forum: General Help
---

### Post by wolfen10862 on 2013-11-23
Is it possible to run two hard drives, on one computer one SATA with Ubuntu, and one IDEE with Windows and have both?
Cause the one and only game I like to play will not run on Liinux, and the developers have no intention of making it for Linux, and I'll be damned if I get rid of this fine operating system and go back to windows, so what I want to do is install a 40 gig hdd put vista on it and leave Ubuntu on the 500 gig hdd and be able to boot from either or.

---

### Post by tgalati4 on 2013-11-23
It's certainly possible.  In general, you want to install Windows first--remove the 500 gb drive so the Windows installer doesn't mess it up.  When you have Windows installed and running the way you want, then plug the second drive into the machine.  You will probably have to edit the grub entries and install grub on first (Windows) drive, but edit the entries to point to the correct drive for each operating system.

Spend as much time here:  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) as you do installing Windows.

---

### Post by wolfen10862 on 2013-11-23
Ok do I install Grub on the windows drive or the Ubuntu drive?

---

### Post by kurt18947 on 2013-11-23
Have you considered installing Windows on a virtual machine?  I don't know how your game will work - I think Windows VMs may be graphics limited but I'm not a gamer so don't know.

---

### Post by mastablasta on 2013-11-23
> **wolfen10862 said:**
> Ok do I install Grub on the windows drive or the Ubuntu drive?

you install it on the drive you boot from. so if you boot in bios first from windows drive then you install it on windows drive. if you install it to wrong drive boot into live ubuntu and just repair the boot with boot repair tool.

---

### Post by wolfen10862 on 2013-11-23
OK I found the problem with the 500 gig hdd and windows vista, the boot sector is corrupt, which tells me Ubuntu doesn't use it :)
Now the big question since I'd love to duel boot and use Windows ONLY for a few games and the real Operating system ( Linux for everything else here's the question, will Gparted erase a windows boot sector?
Yes I AM about to go find out for myself, but I like to verity at my age, ya see, when I was taught, you trust but verify, and if you had any questions you asked the experts ( that'd be yall)

---

### Post by Mark Phelps on 2013-11-24
I've found, when using two physical drives, the most trouble-free arrangement is the following: 
1) one OS on each of the two drives
2) The correct boot loader for each OS on its own drive.

That makes each drive bootable on its own and updates to either OS do not affect the other's ability to reboot.

So, I would NOT put GRUB on the (proposed) Vista drive.  Just disconnect the Ubuntu drive when you reinstall Vista.

Then, reconnect the Ubuntu drive, boot from it, and run "sudo update-grub" in a terminal.  That will regenerate the GRUB confile file in Ubuntu and when you reboot, you will have a GRUB menu with entries for both OSs.

---

