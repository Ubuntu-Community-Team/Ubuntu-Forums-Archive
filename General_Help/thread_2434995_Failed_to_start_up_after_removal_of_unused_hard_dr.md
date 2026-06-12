---
title: "Failed to start up after removal of unused hard drive"
date: 2020-01-14
forum: General Help
---

### Post by 4-null-nan on 2020-01-14
When I removed an un-used hard drive, I couldn't start up Linux.  I wonder if there is a small chance that I did use that hard drive as a boot sector or something to that effect.
I did try to boot up using a gParted disc and I could mount and see the correct hard drive is in the computer.

The error was invalid file system or something like that, and falls back to grub.

I put back the other hard drive and it boots up successfully.

How would I fix this?  Is it by any chance that the two hard drive IDs are generated differently when both are in there and cause problem? 

I would like to have a choice of removing the un-used hard drive if I need it for something else.  Thanks.

---

### Post by CelticWarrior on 2020-01-14
I would say the chance is huge, not small.

BIOS or UEFI? The instructions are different.

---

### Post by 4-null-nan on 2020-01-14
The setup is BIOS.

---

### Post by CelticWarrior on 2020-01-15
So the bootloader is at the MBR of the drive you removed.

Boot with both drives and simply install Grub to the one you want to keep.

---

### Post by 4-null-nan on 2020-01-15
Great.  Thanks.  It works now after install the grub on to the correct drive.

---

