---
title: "Uninstalling grub"
date: 2005-10-11
forum: General Help
---

### Post by crazyj on 2005-10-11
hi

I have a PC with win 2k and ubuntu on it but i need to sell the PC and i want to uninstall ubuntu along with grub as i dont think people will want to buy a PC with linux on it how can I get rid of ubuntu?

Thanks in advance


also i dont have any windows recovery disk ect.

---

### Post by swerner on 2005-10-11
Why not just tell the person that it has Linux on it if they want to try. 

Otherwise, if that fails, you can do a "fdisk /mbr" to refresh the boot record Windows style, then "fdisk" to create a new partition, then "format d:\" or whatever.  Although I don't know if those commands are still available in Win2K.

---

