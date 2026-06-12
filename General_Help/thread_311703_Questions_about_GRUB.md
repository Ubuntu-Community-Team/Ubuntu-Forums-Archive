---
title: "Questions about GRUB"
date: 2006-12-03
forum: General Help
---

### Post by Ultimadark on 2006-12-03
Hello

Today I installed Ubuntu for the first time, and Im wondering, is there any need use a bootloader other than grub? If I would reformat the Ubuntu drive to a NTFS, would I still be able to boot into my Windows installation from GRUB? Im wondering this because I cant get internet to work on Linux and it would be nice to have that space available to windows instead.

Also, if I want to re-install Windows, will there be any problems with GRUB installed then?

---

### Post by podunk on 2006-12-03
Reinstalling Windows will wipe the grub bootloader from your system - which would be the way you want to go if you're going to have a Windows only system.

If you format the Ubuntu drive to delete Ubuntu you can use the recovery option of your Windows install CD to restore the master boot record so it boots up into Windows.

You know - you can get a lot of help on these forums. If you are having connection problems the solutions are usually simple if you post what problem you're having.

---

### Post by pay on 2006-12-03
You can get windows to use it's own bootloader by loading the windows cd and booting into the recovery console then typing ```
fixboot
fixmbr
```

---

