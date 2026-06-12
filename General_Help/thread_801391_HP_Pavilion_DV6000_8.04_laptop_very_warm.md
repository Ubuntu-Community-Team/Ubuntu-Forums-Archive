---
title: "HP Pavilion DV6000 8.04 laptop very warm"
date: 2008-05-20
forum: General Help
---

### Post by Kristopher on 2008-05-20
Ever since 8.04 i am finding that my laptop fans are on a lot more, and the laptop feels warmer to touch. Is this an HP issue or a kernel issue etc? as with 7.10 am sure it wasnt getting this warm and the fans were only on once every now and then.

---

### Post by cwbar_1 on 2008-05-20
Check your bios version with HP.  If you are not at version F.29, (11-2007) your laptop will run hot.

---

### Post by Kristopher on 2008-05-21
Cool thank you, I will try and find the bios and see what I need to do to update it.

---

### Post by pgioun on 2008-09-11
> **cwbar_1 said:**
> Check your bios version with HP.  If you are not at version F.29, (11-2007) your laptop will run hot.

ok...i would like to update my bios (current version f27) but there is no obviously way updating without windows Os...help please

---

### Post by jblackthorne on 2008-09-11
I can confirm the bios update will fix your heat issue.  The new bios updates the fan profile to keep the system a bit cooler.  Still, some heat is to be expected as this machine was engineered to be able to run pretty hot without damage.  

I had the some Windows dilemma too since the HP bios update is WinFlash only.  To get around it, I installed a light copy of WinXP on an external USB drive.  I have A WinXP VirtualBox machine too, but I did not want to trust that for a bios update.  Any way, WinXP on an external USB drive works great and allows for running the bios utilities.  If you don't have an external hard disk, you could probably use a USB memory stick too.  

Good luck!

---

### Post by zoomy942 on 2008-09-11
> **jblackthorne said:**
> I can confirm the bios update will fix your heat issue.  The new bios updates the fan profile to keep the system a bit cooler.  Still, some heat is to be expected as this machine was engineered to be able to run pretty hot without damage.  

I had the some Windows dilemma too since the HP bios update is WinFlash only.  To get around it, I installed a light copy of WinXP on an external USB drive.  I have A WinXP VirtualBox machine too, but I did not want to trust that for a bios update.  Any way, WinXP on an external USB drive works great and allows for running the bios utilities.  If you don't have an external hard disk, you could probably use a USB memory stick too.  

Good luck!

i just noticed that mine has a firmware update too (2710p) and i have a VB of windows.  should i not trust it?

if not, how can i install that lite windows you speak of?  i have never heard of that.

EDIT: I found on the HP site they there were bootable USB versions of the update

---

### Post by Kristopher on 2008-09-12
Cool good to know a BIOS update fixes this issue, how easy is it to update the BIOS? will it destroy Ubuntu files or just effect the BIOS.

I have never done this before, so i would need windows...can this not be done within Virtual Box?

---

### Post by benjick on 2008-09-12
Woho, i work with HP laptops :>

The bios could work but often when we just clean the fans when we get them in. Sometimes we change the fan but this problem sometimes occur when the motherboard is faulty. Rare case tho, so don't worry. Use compressed air in the fans; make sure to lock the fans with something, like a paper clip or something. Good luck

---

