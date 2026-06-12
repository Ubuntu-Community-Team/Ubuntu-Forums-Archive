---
title: "Windows in VMware (GRUB/MBR issue)"
date: 2007-01-25
forum: General Help
---

### Post by blackheart-uk on 2007-01-25
I have two hard drives. hda has Windows XP on it, and hdb: Ubuntu Edgy. GRUB is installed on the MBR of the Windows disk, with the rest of the files in hdb1, which I believe is the default setup for Ubuntu.
I followed the tutorial at [http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm](http://rougebob.com/Running-a-Windows-Partition-in-VMware.htm) to get my Windows partition running in VMware.

Upon booting the virtual machine, I get an error from GRUB (Error 21). I believe this means that it can't get at the files on hdb1.

I've come to the conclusion that:
1: I need to flash my MBR with the Windows boot loader. This way it'll start windows automatically.
2: I then need Ubuntu so that I can use dd to make a copy of the MBR for VMware, as stated in the tutorial.
3: Once that's done, I need to reinstate GRUB in the MBR.

What I'm wondering is can steps two and three both be done from an Ubuntu Live CD? Or is there a way that I can boot Ubuntu from my floppy drive or something? I'm sure it's possible, and I'm sure I've seen the option to do it before, but I need help with the nuts and bolts of it.

I apologise for the length of this, but any help would be greatly appreciated.

---

### Post by blackheart-uk on 2007-01-25
Right I have sorted some of the problem.

I created a GRUB Boot Floppy, this was simple following the instructions at [https://help.ubuntu.com/community/GrubHowto/BootFloppy](https://help.ubuntu.com/community/GrubHowto/BootFloppy)

Then I booted back to Windows, downloaded a Windows ME Boot disk from the net (sorry I can't remember where), rebooted with it in the drive, ran ```
fdisk /mbr
``` and then rebooted with the GRUB disk in the drive. I followed the instructions and did the whole dd thing. The virtual machine starts up but then reboots showing a blue error screen asking if I've changed anything and to check my hard disks. Hmm.

Putting GRUB back is equally easy though, the instructions are at [http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113) although I have yet to do it.

Well, I'll keep trying...

---

### Post by umattu on 2007-01-25
You are getting the blue screen because EVERYTHING has been changed. Your XP install has all of the drivers it needs to run your ACTUAL hardware. When it is run in VMware it is using "virtual hardware" that runs on differant drivers. Installing XP to VMware will no doubt fix this but at the cost of loosing any data or apps that you dont have backed up. Also did you flollow the hardware profile settings in the tutorial?

---

