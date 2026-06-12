---
title: "pci ide controller"
date: 2006-11-27
forum: General Help
---

### Post by eriefisher on 2006-11-27
I'm having a problem booting into WinXP. I have 3 hard drives hda-Linux. hdb-WinXP, hde-vfat for sharing between OS's. My problem is when I try to boot into WinXP I get a grub error 22 "no such partition". If disconnect hde-vfat from the pci ide controller(the only drive on the controller) hdb-WinXP will boot with no trouble. hda-Linux has no trouble either way. I can't seem to figure this out, There should be nothing on the hd to prevent the boot. grub does point to the correct drive but won't see it with the fat drive connected. Some insight would be great.

eriefisher

---

