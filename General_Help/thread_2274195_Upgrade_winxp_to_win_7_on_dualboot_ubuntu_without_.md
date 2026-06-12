---
title: "Upgrade winxp to win 7 on dualboot ubuntu without deleting boot"
date: 2015-04-18
forum: General Help
---

### Post by richlyn9 on 2015-04-18
Hi All,

I have old dual boot system with xp and ubuntu, have never required xp however now require to upgrade to win 7 for work purposes.
GParted snapshot attached.

I firstly dont want to  reinstall ubuntu after installing win7, which may be the case with the Win Install. can i achieve this and how?
secondly i need more space for win 7 can i merge sda2 with boot partition sda1? 
pls guide me.
Thanks!!

---

### Post by mörgæs on 2015-04-19
You have installed using ext3, which could indicate a very old Buntu. If that's the case I suggest a fresh install of first Windows 7 (using NTFS) and then Buntu for the rest (using ext4).

You could also delete XP, merge the two Windows partitions into one NTFS partition and install here without deleting Buntu, but it will take more adjusting to get both systems to boot. Windows does not play nicely with other operative systems.

---

### Post by richlyn9 on 2015-04-20
if i delete the two windows partitions and merge them into one.I ten install win 7 on to this merged partition without deleting ubuntu will the boot menu remember ubuntu?
I think not. What needs to be done if i dont want to reinstall ubuntu?

---

### Post by Impavidus on 2015-04-20
Installing or upgrading Windows is likely to wipe the boot loader and make Ubuntu inaccessible. The easiest way to repair is using [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). But make backups of Ubuntu just in case, as I have heard stories of Windows upgrades wiping Linux partitions.

Your signature line mentions WinXP, Lucid and Oneiric. Have you forgotten to upgrade that? Because if you really use those systems, you have not one but three end-of-life systems and it would be best to clean install Ubuntu anyway.

---

