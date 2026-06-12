---
title: "error: no such device : grub rescue&gt;"
date: 2017-03-10
forum: General Help
---

### Post by lampel on 2017-03-10
hello all ,
i have a pc with win10 installation on it ,
i have installed ubuntu 16.04 on an external HDD ,
now when i start my computer and the external HDD **is connected** to the pc
the grub menu opens and i can choose between win10 or ubuntu ,
the problem is when i power on my pc and the external HDD **is not connected**
i get an error message :
 error: no such device : 
grub rescue>

and i cannot boot the WIN10 ,
i think i have installed the grub menu on the external HDD ,
how can i move the grub installation into the pc ?
how can i fix this issue ?
Thanks lampel

---

### Post by oldfred on 2017-03-10
UEFI or BIOS?
If UEFI, you should be able to directly boot Windows from UEFI one time boot menu.
If BIOS, you need to install grub to external drive and reinstall Windows boot loader to internal drive.

       May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

