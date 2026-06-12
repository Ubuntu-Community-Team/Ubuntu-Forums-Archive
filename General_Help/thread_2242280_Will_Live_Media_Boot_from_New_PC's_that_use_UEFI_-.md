---
title: "Will Live Media Boot from New PC's that use UEFI - w/o user intervention?"
date: 2014-08-31
forum: General Help
---

### Post by JeQhdMD on 2014-08-31
In a few days, I am doing a demo on Live CD-DVD-Flash media to rescue data and prep hdd's before a Linux install.

My 3 systems are pre-UEFI devices so I am wondering if a newer class of laptop will automatically boot from these live media . . . or does the user also have to bring up the device "setup" screens to disable secure boot, etc.

Any clarification on this is appreciated.

Thanks.

---

### Post by cariboo on 2014-09-01
If you are booting from a 64-bit iso, the EFI bootloader is included, so you shouldn't have any problems.

---

### Post by Dennis N on 2014-09-01
Your flash media will boot, but in my experience, not without intervention - that is, using the UEFI system's firmware boot menu. Often there is a key to press on boot up to enter the boot menu directly (just like on a bios system), or else you enter the UEFI bios and from there enter a boot menu. On the boot menu, you select the device to boot and boot mode  (UEFI or bios). 

It's possible you may have to set a 'legacy mode' in some UEFI implementations in order to boot some media - there are a lot of variations between UEFI implementations.

---

### Post by JeQhdMD on 2014-09-02
Thanks for the info.   I am just thinking about using a Live flash-stick with Parted Magic on it, and testing it first on a new workplace laptop.

---

