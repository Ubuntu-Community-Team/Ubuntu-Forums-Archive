---
title: "Edit Grub file(s)"
date: 2019-08-04
forum: General Help
---

### Post by ub-newbie2 on 2019-08-04
Ub 19.04 is successfully installed and running. However it was installed after "MATE" so that in the Grub file Ub is not at the top of the list of dual-boot choices (it appears on lines # 2 & 3 instead of line # 0). Not a "biggie" but this could be a learning exercise for newbie me if the Grub file(s) could be edited so that Ub 19.04 (line # 2) was the default instead of MATE (line 0). I was able to edit the file so that default is now line # 2 where Ub 19.04 appears but apparently the change is not effective since MATE still runs unless Ub 19.04 is specifically chosen from the Grub menu. The cmd "sudo nano /etc/default/grub" allowed the file to be edited. This was followed by "sudo update-grub" but there has been no apparent change in the Grub selection menu - MATE is still the default.

Is this exercise worth the time spent trying to change Grub ?  If so, what else shd i know abt editing Grub file(s) ?  Thanx.

Bewildered Bob

---

### Post by oldfred on 2019-08-04
UEFI or BIOS?

Last install is normally in charge of MBR if BIOS or ESP - efi system partition if UEFI.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

