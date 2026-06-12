---
title: "Disk Read Error - Nothing Is Working"
date: 2013-02-08
forum: General Help
---

### Post by JosephBeck on 2013-02-08
I recently tried to dual boot Ubuntu 12.04 with an old Windows XP System. Instantly after installing upon start up I get "Disk Read Error" then the whole ctrl + alt + del thing. I don't get a grub menu or anything. Oddly, if I keep the usb in that I used to install Ubuntu and boot from that USB it'll bring up the Ubuntu grub menu. It'll work if I choose Ubuntu but if I choose Windows it goes back to the "Disk Read Error". I've tried countless solutions to repair the MBR. I've tried:

Terminal
-Boot-Repair
-LILO

Windows XP Recovery Console
 -Fixboot
 -Fixmbr
 -CHKDSK /R
 -CHKDSK /P

None of it has fixed the issue and I installed Ubuntu following the directions on a distro site. One might think it is installed to the USB since it requires the usb to boot into Ubuntu but that is incorrect. Once booted I can remove the USB and it works fine. Also, I have reformatted the USB and wiped it completely and it still requires me to boot from the USB to load the Ubuntu grub. 

I want to get my Windows XP back, and I'm definitely removing Ubuntu from that computer and never trying to dual boot again. Too much hassle. I do not wish to reformat the entire hard drive and reinstall Windows XP. I need this fixed ASAP.

---

### Post by JosephBeck on 2013-02-08
Bump

---

### Post by JosephBeck on 2013-02-08
Bump x2

---

### Post by Mark Phelps on 2013-02-09
You need to QUIT bumping -- rule of thumb around her is ONCE every 24 hours, not repeatedly.  This is a GLOBAL forum and it could be some time before someone comes along, reads your thread, and provides a response.

---

### Post by tgalati4 on 2013-02-09
What size is the hard disk and how old is it?  A read error may be an indication of a hard disk failure.  Some hard disks read in the firmware on the first few cylinders and won't boot up properly if there is a disk head problem.

When you boot into BIOS (F2 or Del) can you see your hard disk in the list of drives?

Yes, installing a dual-boot system can be a hassle, but if you have wonky hardware, it can be a nightmare.  Most installs go fine.  A few don't.

---

