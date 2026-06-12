---
title: "Looping Vista Bootloader"
date: 2008-06-22
forum: General Help
---

### Post by Skyy on 2008-06-22
Hi guys, 
I gave WUBI a try but I can't get it to work.

My system is dualbooting Vista and XP and partitioned as following:

IDE1 Master

C: Windows XP (NTFS)
E: Data (NTFS)

IDE1 Slave

D: Windows Vista (NTFS)

SATA

H: Wubi is installed here (NTFS)

I installed Wubi in Vista which worked fine and it asked to reboot. When I select the new Ubuntu entry in Vistas bootloader I see alot of text scrolling down VERY fast, thus unreadable, the only word I can read is "chainload" at the end, after that I get back to the Vista Bootloader OS select.
This happens every time I select Ubuntu, Vista and XP boot fine.

Is there a way to fix this?

Also, if I install Wubi from XP, will it alter the Vista loader in any way?

Thanks for help in advance!

EDIT: I just gave the Install from XP a shot, after the reboot I had Ubuntu again in the Vista loader which gave me the same results but when I selected Windows XP I got the XP bootloader with two new options:

Windows XP Home Edition
Ubuntu

when I selected this Ubuntu I got a GRUB4DOS screen with again two options:

Windows Vista
Windows Vista

so where's my Ubuntu?

---

