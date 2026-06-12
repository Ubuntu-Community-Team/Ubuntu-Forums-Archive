---
title: "I messed up! Bottom line, locked out, can't get bios, won't boot ubuntu from usb."
date: 2018-04-25
forum: General Help
---

### Post by mawil10132 on 2018-04-25
I'm updating this, Great luck and progress, I've been able to use the USB - ISO to run off the USB and have a viable ubuntu on screen.  I'm doing install of U16.04.4 LTS over Linux Mint 18.3 Sylvia, I selected Erase disk and install ubuntu------- Then I get; Force UEFI Installation?? This machines firmware has started the installer in UEFI mode but it looks like there may be existing Op. Sys's already installed using "BIOS compatibilty mode". If you continue to install debian in UEFI, it might be difficult to reboot the machine into any BIOS-mode operating system later.  and; If you wish to install in UFEI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here, if you wish to keep the option to boot an existing OS, you should choose NOT to force UEFI here.  (My choices are ; Go Back and Continue in UEFI mode)  I can say that all I want is U16.04.4 so I assume tap Continue >>> Didn't hear from anyone so I tap Continue, and install looks normal, I'm back to where I was,, after rebooting after install i get this message, > Default Boot Device Missing or Boot Failed. Insert Recovery Media and Hit any Key. Then Select "Boot Manager" to choose a new boot device. end of message

At this point all I can do is run Live. and If I attempt to get into BIOS by tapping esc when 'acer splash' appears I get> Enter Current Password




Orig-Post:  Deleted, not relevant an longer.

---

### Post by kerry_s on 2018-04-25
did you set a bios password?
or
did you encrypt your disk & set a password?

---

### Post by mawil10132 on 2018-04-25
> **kerry_s said:**
> did you set a bios password?
or
did you encrypt your disk & set a password?



When I installed ubuntu I did encrypt disk with password, 

I had to alter UEFI in bios to install, unless it required me to set a password, then no,

---

### Post by kerry_s on 2018-04-25
so power off, keep tap "esc" as it powers on, you should be able to get to the bios to set usb to boot first, wipe that drive & install.

---

### Post by mawil10132 on 2018-04-25
> **kerry_s said:**
> so power off, keep tap "esc" as it powers on, you should be able to get to the bios to set usb to boot first, wipe that drive & install.

Same comes up that has been coming up'

default boot device missing or boot failed
insert recovery media and hit any key
then select 'boot manager' to choose a new boot device or to boot recovery media.  (Tap OK)


putting in bootable ubuntu usb brings me back to same message again.

or I get Boot Manager, Boot Option Menu, 1> Fix

I can't get past these two menus except i do get a request for a password, no passwords work.

---

