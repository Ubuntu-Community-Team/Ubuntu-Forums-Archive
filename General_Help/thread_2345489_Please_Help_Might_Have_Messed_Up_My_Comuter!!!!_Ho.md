---
title: "Please Help Might Have Messed Up My Comuter!!!! How to delete Ubuntu on Ubuntu!!!"
date: 2016-12-04
forum: General Help
---

### Post by retro57 on 2016-12-04
Recently i installed Ubuntu to have a dual boot with my windows 10 computer. Ubuntu is working fine. Now whenever i go back into windows i get the blue screen of death. I talked with windows support i now they are saying it is a hardware issue. This happened right after installing Ubuntu. Someone please tell me how to delete Ubuntu off my computer so i can just have a windows computer again. Thank You. 


P.S. Cant go back on windows to delete the Ubuntu partition

---

### Post by oldfred on 2016-12-04
UEFI or BIOS?

With UEFI you should just be able to use UEFI boot menu & boot Windows.

If BIOS, you have to install the Windows boot loader to directly boot Windows. You can use your Windows repair/recovery flash drive and run fixMBR.
       [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) 
    

You probably have Windows fast start up on, or in UEFI have Secure Boot on. Grub menu cannot then be used to boot Windows.

---

