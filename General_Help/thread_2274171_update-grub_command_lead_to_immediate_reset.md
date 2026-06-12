---
title: "update-grub command lead to immediate reset"
date: 2015-04-18
forum: General Help
---

### Post by nobb1x on 2015-04-18
hi, i'm into Ubuntu since quite time, having to change my hdd i have decided to reinstall everything from the scratch. so i switched to a gpt partition table and i'm using a triple boot with macosx yosemite, windows 7 and ubuntu 15.04 beta 2. all 3 os are installed in uefi mode . my bios let me to decide what boot option i want to boot so i choosed to boot the partition containing the Clover bootloader which can boot all 3 OSes with no issues. ok up to now.
Problems starts when i am in Ubuntu, the system works great but everytime i have to update the grub, which reside in the same partition where Ubuntu is (/dev/sda6), issuing the command "sudo update-grub" i have a immediate reset.
This also happen if i use my bios to boot the partition contain Ubuntu, skipping Clover.
i can see on the terminal it print few lines then a fast reset make me impossible to understand what happening.
Being a noob in grub troubles i don't know where to start to try to debug the problem, any idea?
i can post logs and more details if needed. tia

---

