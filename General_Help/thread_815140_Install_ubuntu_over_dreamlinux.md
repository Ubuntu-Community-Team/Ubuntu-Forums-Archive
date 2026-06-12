---
title: "Install ubuntu over dreamlinux"
date: 2008-06-01
forum: General Help
---

### Post by pspfreak101 on 2008-06-01
I want to just confirm but I have dreamlinux installed on hd(0,3) and wanted to know if I should just install ubuntu right over that because I want to leave the grub menu it has or should I format this partion?

---

### Post by kellemes on 2008-06-01
> **pspfreak101 said:**
> I want to just confirm but I have dreamlinux installed on hd(0,3) and wanted to know if I should just install ubuntu right over that because I want to leave the grub menu it has or should I format this partion?

What part of the grub menu do you need to keep?
Personally I'd simply let Ubuntu setup the bootloader, if there is something specific in your current grub-menu you need to keep, you can create a backup of */boot/grub/menu.lst*. This file holds all the entries of your bootmenu.

---

### Post by mikewhatever on 2008-06-01
> **kellemes said:**
> What part of the grub menu do you need to keep?
Personally I'd simply let Ubuntu setup the bootloader, if there is something specific in your current grub-menu you need to keep, you can create a backup of */boot/grub/menu.lst*. This file holds all the entries of your bootmenu.

+1. Leaving the menu from DL will point grub to non existent kernel. Back it up for reference if there are more OSs and format that partition.

---

