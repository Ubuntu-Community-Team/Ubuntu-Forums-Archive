---
title: "Deleted grub"
date: 2019-06-21
forum: General Help
---

### Post by nhrnhr0 on 2019-06-21
Hey, I deleted the partition of my grub. my ubuntu parrtition is still there but I can't access it without the grub. How can I start my ububtu?

---

### Post by oldfred on 2019-06-21
What grub partition?
With MBR, grub does not have a partition.
With UEFI, all boot loaders are in an ESP - efi system partition (FAT32 with boot flag)
Or with newer gpt partitioning and the old BIOS Boot your need a bios_grub partition.

You would need to recreate partition and then do a full reinstall of grub.

       May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

