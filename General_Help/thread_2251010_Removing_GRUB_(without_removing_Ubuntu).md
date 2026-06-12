---
title: "Removing GRUB (without removing Ubuntu)?"
date: 2014-11-01
forum: General Help
---

### Post by tehtotalpwnage on 2014-11-01
Hi there! I'm pretty satisfied with Ubuntu, as it makes an AWESOME platform for video editing and such (very OS X like environment lol). I installed Ubuntu alongside Windows in (U)EFI mode and used Ubuntu to install rEFInd as my boot manager. However, because of this, I no longer have a need to use GRUB, since the GUI for rEFInd looks so much better. Is there a way to remove GRUB so only Ubuntu remains and I no longer see the GRUB boot option in rEFInd? I already tried running "sudo apt-get purge" for grub, grub-pc, and grub-common, and GRUB is still there.

---

### Post by yancek on 2014-11-01
The quote below indicates that rEFind by default chainloads these bootloaders so in your case, if you remove Grub, you will not be able to boot Ubuntu

> I consider ELILO, GRUB Legacy, GRUB 2, and SYSLINUX to be traditional Linux boot loaders. These programs all exist independent of the Linux kernel, but they can load a kernel and hand off control to it. All four programs have their own configuration files that reside in the same directory as the boot loader itself (or optionally elsewhere, in the case of GRUB 2).

If you read the explanations at the rEFind page below, it seems that it is possible. 

[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)

---

### Post by tehtotalpwnage on 2014-11-01
> **yancek said:**
> The quote below indicates that rEFind by default chainloads these bootloaders so in your case, if you remove Grub, you will not be able to boot Ubuntu



If you read the explanations at the rEFind page below, it seems that it is possible. 

[http://www.rodsbooks.com/refind/linux.html](http://www.rodsbooks.com/refind/linux.html)
I've already managed to boot Ubuntu without GRUB, since there are 3 options to boot Ubuntu by default. These are the GRUB bootloader and then two VMLinux options. I selected one of the VMLinux options and it booted without having to enter the GRUB screen, so it should be alright to remove GRUB.

---

### Post by oldfred on 2014-11-02
I have read some of the rodsbooks links, but do not know details.

Did you copy kernel into efi partition? I thought that was a requirement to have UEFI directly boot Linux or does rEFInd avoid that?

Grub in UEFI boot mode is grub-efi-amd64. The grub-pc package is the BIOS boot version.

I would backup efi partition and grub before uninstalling.

---

