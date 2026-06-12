---
title: "Secure Boot. Can one use it for a singular Ubuntu install on disk?"
date: 2015-10-18
forum: General Help
---

### Post by mikodo on 2015-10-18
Hello everyone.

Is there an option to leave Secure Boot *on, in UEFI with Ubiquity? I've never used efi or UEFI in the past if, this question is rudimentary.

Paraphrasing oldfred, from another thread and, *not use "a standard UEFI or even just BIOS/Legacy/CSM" for a new install of Ubuntu only. 

I am thinking of this for my *next Desktop machine. (Probably from System76 or maybe ZaReason). 

Or, should I wait until I have purchased the machine first before, asking what my options are?

I've recently read, there are some advantages of Secure Boot such as, helping thwart Bootkits.

Thank you.

---

### Post by grahammechanical on 2015-10-18
Secure boot is part of the Unified Extensible Firmware Interface (UEFI). Turning secure boot on or off is done in the UEFI settings utility. Ubuntu has been able to handle the requirements of secure boot since the release of Ubuntu 12.10. Manufacturers do not always comply completely with the UEFI specification. This is why with some models of computer dual booting is more tricky than with other models. And from some posts on this forum it seems that turning secure boot off solved a dual booting problem.

From what I have read the main issue with dual booting on a machine with Windows 8 or Windows 10 installed is not so much as to whether secure boot is on or off but as to whether the existing OS was installed in EFI mode. In the case of Windows it is installed in EFI mode and that means Ubuntu will have to be installed in EFI as well.

On a machine without any OS pre-installed Ubuntu can be installed in EFI mode or BIOS/CSM/Compatibility mode depending on what you want. This issue is nothing to do with secure boot. I would agree that there are most definitely advantages to having secure boot on.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> "[Secure Boot]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface#Secure_boot")" is a new UEFI feature that appeared in 2012, with Windows8 preinstalled computers. All current Ubuntu 64bit ([not 32bit]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555"))  versions **now support this feature**, but as PCs implementing support for  it have only become widespread at the end of 2012 it is not yet widely  tested, so it's possible that you may encounter problems booting Ubuntu  under Secure Boot.  If you do, please file a bug report against the [shim]("https://bugs.launchpad.net/ubuntu/+source/shim/") package in Ubuntu, preferably using the command ubuntu-bug shim once you've installed with Secure Boot disabled.

This explains the process used in Ubuntu.

[https://wiki.ubuntu.com/SecurityTeam/SecureBoot](https://wiki.ubuntu.com/SecurityTeam/SecureBoot)

Regards.

---

### Post by mikodo on 2015-10-18
Graham. Thank you.

You've answered my questions, "in spades".

I am *pleased, I probably can have what I want. 

Now, after reading the links for starters, I will know what to ask of the retailers, before buying their machine.

Have a nice remainder of the evening!

---

