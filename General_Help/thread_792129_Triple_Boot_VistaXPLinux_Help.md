---
title: "Triple Boot Vista/XP/Linux Help"
date: 2008-05-12
forum: General Help
---

### Post by archer007 on 2008-05-12
I would like to triple boot my hp laptop with Vista (pre-installed OEM), XP, and Linux. I want Vista to have a drive to itself, and XP and Linux to share a secondary NTFS/linux drive. However, I am extremely wary of replacing the Vista bootloader. 

I think I just have to do the following: boot into Ubuntu, make my second drive have an NTFS and linux filsystem partition, install Ubuntu on the linux partition in the secondary drive, and then boot into and install XP from the CD onto the NTFS partition on the secondary drive.

Afterward, GRUB should be the default bootloader, and "see" both XP and Vista.

Is any of that wrong? Does GRUB let you change boot order and default OS to boot? I am particularly worried that GRUB will not auto-recognize Vista and/or XP, which would mean I would have to fool around with it forever until it does. I have the Ubuntu 8.04 disc, a Windows XP SP2 disk, and the first CD for Vista Business Edition. Will the CD for Vista Business Edition work if I need to recover the bootloader for my copy of Vista? I have Home Premium.

---

### Post by Patrick793 on 2008-05-12
Grub should automatically find Vista and XP. The default OS in grub is the one it was installed by, but, you could easily go on Vista, and use EasyBCD to reinstall the Vista Bootloader, and add an entry for Ubuntu, and one for XP if it doesn't detect it automatically.

---

### Post by rogthewookiee on 2008-05-12
I am currently triple booting and I didn't have ny problems with grub. I did edit the menu.lst so it would boot to XP first. With Vista you can roll back what ever drive it is on and put XP and ubutu on the created space.

---

### Post by archer007 on 2008-05-12
Okay, so as long as I have the relevant recovery stuff, I should be good as long as I go for non-destructive partitioning. I'm just afraid GRUB will install itself over the Vista bootloader on my first drive (with Vista) and then somehow mess it up. 

How would I manually add entries to GRUB if it came down to that? By using EasyBCD?

---

### Post by archer007 on 2008-05-14
EasyBCD is NOT a bootable CD, so how would I use it to recover my Vista bootloader if it was damaged or destroyed?

---

