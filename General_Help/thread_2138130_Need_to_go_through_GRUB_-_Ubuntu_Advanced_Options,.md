---
title: "Need to go through GRUB - Ubuntu Advanced Options, if not i boot to black screen."
date: 2013-04-23
forum: General Help
---

### Post by fnurk on 2013-04-23
When I turn on my computer (Acer Aspire 3820T), as the title says, I only get a black screen unless I hold SHIFT and go through GRUB and select the topmost option in Advanced options for Ubuntu. If I select Ubuntu in GRUB I get the same black screen. Anyone got any ideas on how to fix this?

---

### Post by audunpoi on 2013-04-23
I have no idea why that happens, but maybe you could try "boot-repair"? 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by grahammechanical on 2013-04-23
The first option in the Advance Options sub-menu is usually the same as the Ubuntu option. There is something that you can check. 

1) At the Grub menu select Ubuntu and press E that will put Grub into Edit mode. Make a copy of the boot parameters.

2) Use Esc to back out and select Advanced options and select the topmost options and again press E. Make a copy of the boot parameters.

3) Compare the 2 sets of boot parameters. They should be the same. You should be getting the same issue with both options.

Another thing to try is to boot into Ubuntu (anyway you can) and run

```
sudo update-grub
``` and ```
sudo grub-install /dev/sda
``` that is if you only have one hard disk and it is the first hard disk in the system.

That will re-write the Grub Configuration files and re-install Grub into the MBR of sda. You machine is not EFI, is it? Other rules may apply.

Regards.

---

### Post by fnurk on 2013-04-23
> **grahammechanical said:**
> 
Another thing to try is to boot into Ubuntu (anyway you can) and run

```
sudo update-grub
``` and ```
sudo grub-install /dev/sda
``` that is if you only have one hard disk and it is the first hard disk in the system.


That worked a charm! Thank you very much!

---

