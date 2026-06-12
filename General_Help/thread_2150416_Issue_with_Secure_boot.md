---
title: "Issue with Secure boot"
date: 2013-06-01
forum: General Help
---

### Post by curiousgally on 2013-06-01
Hi,

I have the following issue. I'm trying to dual boot Windows8 and Ubuntu with UEFI with secure boot. I have 2 drives, one hdd and another an SSD.  I got the hdd pre-installed with Windows8 setup with UEFI and Secureboot. I want to install ubuntu on the SSD and make both the OS work together. I did some googling and this is what I did.

1) When I had the windows drive and installed Ubuntu on the SSD things didn't work meaning it would install properly but grub wouldn't start. Even I tried to boot-repair but it didn't work. So I removed the Windows hdd and installed Ubuntu on SSD.
2) Installing Ubuntu in UEFI mode with only SSD present was in itself a failure. I tried it with 13.04 version and it never worked. It wasn't installing ubuntu in EFI mode. So I had to do the install with a 12.10 and then upgrade it to 13.04 which works fine for the UEFI setup.
3) Now when I put the windows drive back, the grub is broken. I cannot see the grub at startup.
4) So I again tried using boot-repair. Boot-repair disk never loads if the SecureBoot is on. So I disabled SecureBoot and then tried to boot-repair. It worked fine, grub displays and able to login to Ubuntu. But the same doesn't work with SecureBoot is enabled. 
5) next in boot-repair I chose 'Advanced options' and then maully ticked the 'Secure Boot' check box (it wasn't checked as I disabled secureboot  to be able to boot the boot-repair disk :)) and ran the boot-repair. In this scenario it doesn't show the grub either with SecureBoot enabled or disabled.

Can somebody help me figure out what I'm doing wrong here. I'm using a Lenovo Thinkpad T530 for this setup.

Thanks.

---

### Post by 2F4U on 2013-06-01
All current 64 bit versions are supposed to support Secure Boot. 

[https://help.ubuntu.com/community/UEFI#SecureBoot](https://help.ubuntu.com/community/UEFI#SecureBoot)

If it doesn't work for your configuration, you should file a bug report as described in the Wiki.

---

### Post by grahammechanical on 2013-06-01
When you put the HD with Windows on it back in the machine did you remember to set boot priority to the SSD?

---

### Post by curiousgally on 2013-06-01
> **grahammechanical said:**
> When you put the HD with Windows on it back in the machine did you remember to set boot priority to the SSD?
Ya grahammechanical I have done that. When I put Windows HD back I don't get the Grub at all, neither windows nor ubuntu boots. Just a bios screen which asks me to select a disk to boot from. Selecting either Windows or Ubuntu from this screen results in nothing but reloading of the same screen again.

Thanks.

---

