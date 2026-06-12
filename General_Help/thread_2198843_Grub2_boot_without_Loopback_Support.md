---
title: "Grub2 boot without Loopback Support"
date: 2014-01-10
forum: General Help
---

### Post by William_Jonah_Roberts_ on 2014-01-10
Something went wrong and now I find myself at a Grub 2.00 Ubuntu screen when powering on.  I have a UEFI board, and for some reason, I cannot boot USB.  With all of that said, I have done some research, and found that I can boot ISO's or I can boot from a USB within grub2.  The problem that I have run into is that the standard grub2 that is on my system does not have loopback support.  

I have tried following this as a guide to help mount the ISO, but it isn't working.  [http://wiki.grml.org/doku.php?id=rescueboot](http://wiki.grml.org/doku.php?id=rescueboot)

Additionally, when I try a liveusb stick, I can set the linux and initrd variable, but when I type boot, the machine just reboots back to the grub2 console never booting into the live environment.  So, my question is;

How can I boot an ISO file without loopback support?  I have an ISO image on my storage partition and I can see it when I set root in the grub console.

---

### Post by oldfred on 2014-01-11
Grub2 has loopback, but now sure how well it works with UEFI.
And it does not look like your ISO has UEFI support.
You may be able to boot in BIOS mode, but if trying to repair a UEFI install you need to boot in UEFI mode.

What is it you are trying to do?

If you are just trying to repair your install, this boots in UEFI or BIOS mode.
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

