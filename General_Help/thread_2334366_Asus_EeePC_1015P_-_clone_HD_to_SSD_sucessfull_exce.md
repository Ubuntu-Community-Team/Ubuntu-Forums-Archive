---
title: "Asus EeePC 1015P - clone HD to SSD sucessfull except for Win10 boot"
date: 2016-08-18
forum: General Help
---

### Post by makem2 on 2016-08-18
Using ddresue, I have cloned the internal 250GB HD to a 250GB SSD. Grub boots xubuntu correctly and everything appears in order. However, booting into Win10 produces an error:

error: no such device; BCFA0B15FA0ACC18
Setting partition type to 0x7
error: invalid signature
Press any key to continue.

No yey pressed returns to grub.

gparted shows:

sda1 [red exlamation mark] ext4 100MiB
sda2 [red exclamation mark] ntfs 70.69GiB

All other gparted entries appear correct

Win10 folders are all present and readable from xubuntu.

Grub entries are:

Ubuntu
Advanced options for Ubuntu
Memory test
Memory test
*Windows 10 (loader) (on /dev/sda1)

I am wondering if the error lies in grub and can be corrected, or does Win10 need a repair?

EDIT: a grub-update command produces a set of grub entries minus the Win 10 entry

---

