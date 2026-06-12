---
title: "Problem By Windows 7 boot loader"
date: 2015-12-13
forum: General Help
---

### Post by RezaOptic on 2015-12-13
I New in Ubuntu  I install Ubuntu whiteout any error and now i see my windows 7 from list  of Operation system  but after i select windows 7 don't work and again  load list of Operation systems. How can i fixed from Ubuntu or i must install windows 7 again ? Sorry for my English you can see from video my problem. Tanks [https://youtu.be/VNIaYX36EZk](https://youtu.be/VNIaYX36EZk)

---

### Post by oldfred on 2015-12-13
That looks typical of grub installed to Windows partition.
But we need details, do not run any fixes until someone has reviewed the report.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

If you installed grub to NTFS partition boot sector:
       
 [HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

---

### Post by RezaOptic on 2015-12-13
> **oldfred said:**
> 
 [HowTo] Repair the bootsector of a Windows partition  - YannBuntu
[https://help.ubuntu.com/community/BootSectorFix](https://help.ubuntu.com/community/BootSectorFix)

this link fixed windows7 boot but now Ubuntu is gone.
i must install Ubuntu again ? if yes how can install Ubuntu with windows 7 dual boot my laptop is bad i cant use VM ware.

---

### Post by oldfred on 2015-12-13
Again details would help a lot.

If you install grub to the partition boot sector(PBR) not the MBR. Then you were probably using the Windows boot loader to load the Windows PBR which then had grub2's boot loader.
Restoring Windows correctly to PBR left Windows boot loader in MBR.

BIOS based systems can only boot from MBR and whatever system is in MBR is in control. And Windows is not really designed for multiple booting where grub2 is.

Install grub2 to MBR.

       How to restore the Ubuntu/XP/Vista/7/8/10 BIOS bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by RezaOptic on 2015-12-14
> **oldfred said:**
> 
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

this link fixed my problem Tanks a lot :)

---

