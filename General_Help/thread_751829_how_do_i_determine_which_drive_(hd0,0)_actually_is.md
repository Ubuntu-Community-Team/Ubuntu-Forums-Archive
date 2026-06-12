---
title: "how do i determine which drive (hd0,0) actually is?"
date: 2008-04-10
forum: General Help
---

### Post by bluepowder7 on 2008-04-10
alright, a seemingly simple question, but how do i determine what (hd0,0) actually is in my hard drive collection?  in my desktop, i have 3 hard drives - an IDE and two SATAs.  now, when i'm installing 7.10 all over again onto one of my SATA drives (ditching 32-bit install and putting on a 64-bit install), at the end of the setup windows it asks me where to install the grub boot loader, and it defaults to (hd0,0).  is that the SATA drive, or the IDE drive?  if SATA drive, which one?  i ran through the install with that default, and booting up gives me two GRUB errors - i get error 15 when trying to launch ubuntu, and error 22 when trying to do the win2k / winxp loader.

IDE = 40G = gonna use it for storage only, no OSes on it
SATA1 = 160G = main drive, has Win2k, WinXP, and 7.10, and it needs to be the boot drive
SATA2 = 100G = temporarily stuffed here, my laptop blew up, so i'll be moving files over from it to either the IDE or SATA1 once 7.10 is installed

so, what's (hd0,0)?  is SATA1 going to be (hd0,0), or is it (sd0,0), or something else?

---

### Post by Jose Catre-Vandis on 2008-04-10
Don't know the full answer, other than checking fdisk etc. Easy fix though. Switch off and Unplug the IDE and Sata2 drives. Reboot with live CD. Open terminal.
```

grub
find /boot/grub/stage1
(this returns the location of your grub install (hd?,?)
root (hd?,?) #(uses the information from above)
setup (hd0)
quit
```
reboot. Switch off and plug other drives back in. Start up.

---

### Post by bluepowder7 on 2008-04-11
hmm, tried that and it told me it can't find grub.  so, it must have shoved it onto the IDE drive instead of the SATA drive.  and since BIOS is set to boot from SATA, grub isn't being found or used at all.

i redid the install after unplugging all the other hard drives (so only had the SATA1 drive hooked up), and with the default "install grub loader onto (hd0)" it all worked well.  so far, at least.  i have yet to plug the IDE and other SATA drives back in...

---

### Post by Jose Catre-Vandis on 2008-04-12
If you reinstalled without the other drives attached you will have to manually enter the other two into /etc/fstab when you reconnect, in order for them to be mounted when you boot up.

---

### Post by bluepowder7 on 2008-04-12
yeah, gonna get around to doing that.  thankfully, the laptop drive with its dozen or so partitions doesn't stay in the desktop machine for more than a day, so the only entry to add to the fstab is the 40G IDE drive, which is just one partition.  easy enough even for me to handle!

---

