---
title: "Help, my ubuntu partition doesn't start!"
date: 2006-12-06
forum: General Help
---

### Post by Freddd on 2006-12-06
I was running an application in Ubuntu (Code::Blocks) that hanged and my system freezed totally, so there was nothing to do than hitting the power off button on my computer.

When starting the computer and choosing one of the two alternatives (in Grub) Ubuntu or Ubuntu recovery mode I get this error when selecting one of them:

"Error 18: Selected cylinder exceeds max supported by BIOS"

> 6. Grub Error 18

Situation

Code Listing 6.1: Grub Output

kernel (hd1,4)/bzImage root=/dev/hdb7

Error 18: Selected cylinder exceeds max supported by BIOS

Solution

This error is returned when a read is attempted at a linear block address beyond the end of the BIOS translated area. This generally happens if your disk is larger than the BIOS can handle (512MB for (E)IDE disks on older machines or larger than 8GB in general).

Try an update for your BIOS and/or move your boot partition to the front (or at least into the appropriate range). 

My windows partition still works so my idea was to copy my important files in some way from windows? I have tried the application Ext2 IFS but it doesn't work. I have run their diagnosis application and it says that my partition still have some transactions left and can't be mounted.

I thought about mounting the partition in Windows with the Ubuntu Live CD. Is it possible? Or is there any other way to solve my boot problem? I need my important files..

---

### Post by Freddd on 2006-12-06
Just like that, without doing anything I'm able to access the partition from Windows. Do you think a reinstall of ubuntu will help? I got a lot of "bugs" when upgrading from dapper to edgy, so maybe it's worth it to make a fresh install.

---

