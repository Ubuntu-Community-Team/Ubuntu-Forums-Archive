---
title: "Saved HDD from burned motherboard-Can't boot now"
date: 2017-06-06
forum: General Help
---

### Post by dunya on 2017-06-06
Long story short; motherboard burned, saved HDD unharmed from the notebook. It was a dual boot of xubuntu and win8.

Trying to save some information in this hdd and plugged it as an external hdd to my new computer. I can see the grub, choose ubuntu but I am getting the error "attempt to read or write outside of disk hd0, you need to load kernel first"

Is there any way to boot ubuntu with this hdd?

---

### Post by oldfred on 2017-06-06
UEFI or BIOS hardware?
Ubuntu & Windows installed in UEFI or BIOS boot mode?

       May be best to see details, you can run from Ubuntu live installer or any working install, use ppa version not ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dunya on 2017-06-08
Well, the problem is solved. In my new notebook, Lenovo, it does not work out but most of the other computers that I tried succesfully booted Ubuntu and Windows on the HDD.

---

