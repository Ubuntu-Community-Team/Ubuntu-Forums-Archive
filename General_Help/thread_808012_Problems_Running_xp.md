---
title: "Problems Running xp"
date: 2008-05-26
forum: General Help
---

### Post by steve34 on 2008-05-26
The problem that I am having is I tried to boot windows and got "autochk program not found" then it went to a screen that said "c000021a fatal system error 0xc000003a (0x00000000 0x00000000). So I just got done googling it and it says it is a common error for people dual booting with linux. (Which I am). It says that the nfts file system is hidden... Does anyone know of a simple way to fix this? Thanks.

---

### Post by geo909 on 2008-05-26
Did you have that immediately after you installed ubuntu?

Wait a little to get some thorough answer here. If you don't,
consider trying supergrubdisk in case its grub's problem
(grub is the bootloader that ubuntu installs in your disk).

But wait a little, maybe it's simpler.

EDIT: Supergrubdisk is a live cd that can help you instal/reinstall/fix your grub. I don't remember the webpage, please google it.

---

### Post by steve34 on 2008-05-26
No, windows actually worked fine for a few weeks then I got the error...

---

### Post by jimbob on 2008-05-26
You can check the flags on the partition using Gparted to see if the hidden flag is set and if it is, reset it.

In Gparted select Partition->Manage Flags and uncheck the hidden box.

---

