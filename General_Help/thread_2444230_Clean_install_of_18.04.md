---
title: "Clean install of 18.04"
date: 2020-05-27
forum: General Help
---

### Post by Quarkrad on 2020-05-27
I installed 20.04 on one of my machines and now need to go back to 18.04.  I've hit trouble because the installer keeps dropping out because there is no efi partition.  I do not dual boot on this machine - only have ubuntu installed.  Currently have two partitions on the hd, one for / and another for /home.  How do I install with the normal live usb, with separate / and /home and not keep getting this efi partition issue?  Thanks.

---

### Post by CatKiller on 2020-05-27
Create an EFI partition. More information [here.](https://help.ubuntu.com/community/UEFI)

---

### Post by Impavidus on 2020-05-27
If you install in uefi mode, you need an efi partition. This tells us that you booted the live disk in uefi mode, but have your old system installed in legacy mode. Either create an efi partition or switch to legacy mode. Uefi mode is the modern way.

BTW, your 20.04 /home partition may contain config files incompatible with Ubuntu 18.04. You may have to reconfigure some applications.

---

