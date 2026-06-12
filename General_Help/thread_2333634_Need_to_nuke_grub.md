---
title: "Need to nuke grub"
date: 2016-08-11
forum: General Help
---

### Post by rustychest on 2016-08-11
I sudo rm rf /* 'ed an ubuntu install to wipe the drive to get a clean drive but did a bad job and when I restarted I got the grub rescue>. 

Grub doesn't allow for the bios to open normally, I normally call for a command line and fwsetup but that isn't working. I have searched all previous threads and none cover in detail

What do I do if I can't boot from an usb and have a nuked ubuntu install?

---

### Post by ajgreeny on 2016-08-11
We need a lot more info about your hardware and situation if we are to help you.

Does the computer use the legacy BIOS or UEFI?
Was Ubuntu the sole OS on the machine or is it a dual boot system?
Have you tried repeatedly pressing Shift for BIOS or Esc for UEFI at power-on to get to the BIOS/UEFI setup?
Does your machine have a one-time keypress to show a menu for boot-device priority?
What happens if you use **fwsetup** command at the grub-rescue prompt?

---

### Post by CatKiller on 2016-08-11
GRUB has no influence over the BIOS loading.

---

