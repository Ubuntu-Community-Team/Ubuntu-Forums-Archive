---
title: "trying to uninstall ubuntu, deleted partition in windows but partition still shows"
date: 2018-11-15
forum: General Help
---

### Post by eddy43256 on 2018-11-15
so basically i installed ubuntu, i wanted to get rid of it today so i followed a guide, and deleted the partition etc.. and i deleted the grub files from the efi partition as well. some how the "ubuntu" partition is still being shown in the BIOS boot menu but not anywhere else. pls help

---

### Post by oldfred on 2018-11-15
UEFI has its own NVRAM memory.
So you have to also delete the UEFI entries.
You should be able to do that in your UEFI.

If using Ubuntu, you just need to use efibootmgr.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

---

