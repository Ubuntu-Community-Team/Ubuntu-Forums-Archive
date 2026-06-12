---
title: "Boot into windows 8 using gnu grub"
date: 2015-06-23
forum: General Help
---

### Post by Ayushi on 2015-06-23
My laptop had windows 8.1 along with ubuntu 15.04. I wanted to remove ubuntu so I deleted the partition and rebooted the system. Now it goes directly into gnu grub. And I don't have windows 8.1 recovery disc.

The screen shows this:

GNU GRUB version 2.02~beta2-22ununtu1
minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions. 

Grub>



What should I do?

---

### Post by oldfred on 2015-06-23
One you get Windows working, make that Windows recovery flash drive. Even Windows needs repairs.

Since UEFI install, you should be able to just go into UEFI and in UEFI boot tab choose to make Windows first entry.

To totally remove Ubuntu, you have to also remove it from UEFI and from the efi partition. As long as you have the ubuntu folder in the efi partition it will keep getting added to UEFI's NVRAM as a boot option.

Some UEFI may let you delete entry from UEFI boot menu tab.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo apt-get install efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
Examples:
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)

In the efi partition, delete this entire folder, do not delete /EFI/Microsoft or /EFI/Boot:
/EFI/ubuntu

---

