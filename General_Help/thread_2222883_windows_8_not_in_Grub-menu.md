---
title: "windows 8 not in Grub-menu"
date: 2014-05-08
forum: General Help
---

### Post by frankyboynl on 2014-05-08
Hi, I have my laptop installed with Ubuntu/Windows 8, but somehow I screwed my windows partition, so now it doesn't appear in the Grub-menu. sudo update-grub doesn't work, so how can I restore my dualboot?


thanks in advance, Frank

---

### Post by Mark Phelps on 2014-05-08
It might simply be because preinstalled Win8 machine are nearly always UEFI which presents problems on installation due to the variety of options.  Plus, I think Boot Repair has problems repairing UEFI boot problems.  But, I don't have details because I have avoided UEFI machines.  Sorry, but you'll have to wait until a UEFI-knowledgeable person comes along.

---

### Post by oldfred on 2014-05-08
Post link to BootInfo report from this:
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by newbie2244 on 2014-05-08
What does your grub menu look like - what are the options that it lists?

---

### Post by GeorgeLSpencer on 2014-05-09
I heard that Windows 8 uses a secure boot and so won't probably boot correctly from the grub menu. The experts at the time, not myself included, suggested that the secure boot could probably be turned off in the bios to make the system dual bootable. Unfortunately, or fortunately, depending upon ones point of view, I am booting between three disks with Windows XP, Windows 7 and Ubuntu 12.4, so I really cannot help with your boot to Windows 8. Does anyone know more about the boot process in Windows 8?

George

---

