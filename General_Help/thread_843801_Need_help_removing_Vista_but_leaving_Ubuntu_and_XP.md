---
title: "Need help removing Vista but leaving Ubuntu and XP intact"
date: 2008-06-28
forum: General Help
---

### Post by CP` on 2008-06-28
I installed XP , Vista and Ubuntu in that order. I would like to remove Vista but leave XP and Ubuntu intact. I was thinking of just using EasyBCD to remove the Vista MBR but I don't know if that would screw up GRUB and then I wouldn't be able to access XP. Does anyone know what will happen if I do this or what I have to do to accomplish my goal?

---

### Post by Dzenhax on 2008-06-28
There are better soloutions than mine, but if a better one doesn't come along you can go two ways.  Both start with backing up your data.

Then you can delete the vista partition and resize the other partitions with gparted.  Vista will still appear in your OS list, you just don't select it.  If you do by accident, you can reboot.

There IS a way to edit grub to wipe the vista install from the offered OS stuff but I don't know it off hand.  Whenever I have to edit grub, I look it up all over again.

The other option is to just reinstall after your data backup.  I'm sure that one was a no brainer.

---

### Post by Computer Guru on 2008-06-29
EasyBCD uses the Vista bootloader to store the dual-boot configuration. If the folder "BOOT" is on the Vista drive, then formatting the Vista drive will result in an inability to boot into either OS.

If the "BOOT" folder is on the XP drive, then you can format the Vista partition and continue to use EasyBCD (albiet from within Windows XP) to dual-boot between Ubuntu and XP.

Otherwise, you're going to have to trash the Vista partition, then follow the steps to manually recover GRUB to the bootloader via the live CD and set up a new dual-boot environment from there.

If you had XP first then you put Vista you should have the BOOT folder on the XP drive and therefore you shouldn't have any problems dual-booting after trashing the Vista partition.

Good luck.

---

### Post by hyper_ch on 2008-06-29
I'd get supergrub cd and ubuntu desktop cd... with the ubuntu desktop cd you could then remove the vista partition and create a new one and with the supergrub disk you can then reinstall grub which will install the according entries for xp and ubuntu

---

