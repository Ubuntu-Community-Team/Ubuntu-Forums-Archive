---
title: "Installing Windows 8 on Ubuntu HDD for dual-boot"
date: 2014-05-02
forum: General Help
---

### Post by Mazate on 2014-05-02
Hi there

I'm wanting to install Windows 8 as a dual boot situation.  Currently I have 14.04 installed.  I've never done a dual boot when Ubuntu was the first OS installed so this is new territory for me doing it the other way around.  Is it just a question of creating a partition and installing Windows or do I have to manually do domething to the grub?

---

### Post by drink1297 on 2014-05-02
My son did this, after I told him not to...you just have to keep NTloader from overwriting GRUB, and then after you get windows installed, re-initialize grub

---

### Post by Mazate on 2014-05-02
You wouldn't happen to have any instructions on how to do that, would you?

---

### Post by oldfred on 2014-05-02
I do not think there is a way to stop Windows from overwriting MBR. But reinstalling grub is easy if you have a Ubuntu live installer, Boot-Repair CD, or Supergrub. ( have all of them just in case).

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

      
 [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
With supergrub you can boot into system and then reinstall grub to sda (if drive is sda).
Only from inside a working install:

 sudo grub-install /dev/sda

Windows has to have a primary NTFS formatted partition with the boot flag.
And if you have Linux partitions inside an extended partition as logicals, it may rewrite partition table without the Linux partitions as it does not see them.
Just in case make a backup of partition table. Do this after any resize as if you use to to restore it must have the same partitions with the same sizes and formats.

 Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

