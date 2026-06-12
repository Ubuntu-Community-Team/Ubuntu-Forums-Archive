---
title: "Put Ubuntu HD from dual boot pc to new pc can't dual boot"
date: 2013-11-28
forum: General Help
---

### Post by 1701funi on 2013-11-28
I was dual booting windows 7 and Ubuntu with two HD's until Motherboard died.  Put HD with Ubuntu in new computer as second drive.  If I changed the BIOS so Ubuntu HD was first I got the menu to pick which OS to boot.  Ubuntu booted ok but when I tried windows it would come up.  Do I have to reinstall Ubuntu or is there a repair I can do.

Thanks.
Don

---

### Post by fantab on 2013-11-28
Is Ubuntu booting on the new machine?
I don't think Windows will boot on a new hardware. You may have to re-install Windows.

---

### Post by Mark Phelps on 2013-11-28
Windows will generally NOT boot when you transfer a drive to a PC with different hardware.  There are tools out there that will allow you to "migrate" an existing Windows setup to a different PC, but they require a CD or USB stick of the drivers needed for the new PC and they generally cost money.

---

### Post by 1701funi on 2013-11-29
Ubuntu will boot from the menu if I make it the first drive in the BIOS.  Window 7 is on the primary drive and is a new install.  I did it before putting the hard drive with Ubuntu, in.  When I created the dual boot on the old pc windows was already installed.  I put in a new HD and installed Ubuntu.  Do I have to re install Ubuntu?

---

### Post by oldfred on 2013-11-29
Set BIOS to boot Ubuntu as default and boot Ubuntu.

The current Windows entry is looking for your old install. Just run this and it should update to boot your new install.

sudo update-grub

---

### Post by sdowney717 on 2013-11-29
MS windows protection kicks in to prevent booting MS windows on new hardware.
OS shutdown is to protect MS profits, otherwise cloned drives would boot all over for free.

---

