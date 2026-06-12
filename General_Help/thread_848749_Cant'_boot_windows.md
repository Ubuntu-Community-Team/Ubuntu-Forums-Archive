---
title: "Cant' boot windows"
date: 2008-07-03
forum: General Help
---

### Post by Dpaulson on 2008-07-03
I recently installed linux and now cannot boot my vista partition, I have no idea what to do about menu.lst, all the guides I have gone with dont work. im pretty sure I still have vista because when I enter the command fdisk -l I get: 
Device Boot     Start     End     Blocks     Id     System
/dev/sda1           1   12725  102209520      7  HPFS/NTFS
/dev/sda2       18144   19457   10554705      7  HPFS/NTFS
/dev/sda3       12726   18143   43520085     83      Linux

any help would be great

---

### Post by AnarkistNZ on 2008-07-03
This may help: _[Dual booting Vista and Ubuntu (Vista installed first)]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")_

If I remember correctly (and this is just from memory when I was tri-booting XP/Vista/Ubunutu), GRUB will happily be able to boot between the two. It's just a matter of specifying the correct partition that Vista resides on.

---

### Post by VMC on 2008-07-03
> **Dpaulson said:**
> I recently installed linux and now cannot boot my vista partition, I have no idea what to do about menu.lst, all the guides I have gone with dont work. im pretty sure I still have vista because when I enter the command fdisk -l I get: 
Device Boot     Start     End     Blocks     Id     System
/dev/sda1           1   12725  102209520      7  HPFS/NTFS
/dev/sda2       18144   19457   10554705      7  HPFS/NTFS
/dev/sda3       12726   18143   43520085     83      Linux

any help would be great

Output your menu list from a Terminal:

```
cat /boot/grub/menu.lst
```

Nera the bottom you should see mention of Windows.

---

### Post by dodle on 2008-07-03
Could you post the entries in your /boot/grub/menu.lst.

---

