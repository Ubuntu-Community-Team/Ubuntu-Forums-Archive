---
title: "USB drive boots from one machine, but not others (grub installed)"
date: 2020-02-08
forum: General Help
---

### Post by palex1919 on 2020-02-08
So I have an portable USB 1TB hard drive that I created via clonzilla from a partition on a PC. The boot loader is on some other internal drive. I (maybe naively) though that if I installed Grub on the portable drive (also grub-mkconfig) that it would boot on any other computer. Does not happen. What to do?

PS One a side note, when the USB drive is attached to the 'home' PC, i cant boot into the original partition. UUID conflict? Something else?

---

### Post by sudodus on 2020-02-09
Are you booting in UEFI mode or the old BIOS mode (alias CSM alias legacy mode)? What you tried should work in BIOS mode, but it is more tricky in UEFI mode.

In UEFI mode the problem can be solved, when the internal drive is disconnected, so that the system 'has to' install the boot system (the EFI system partition and its files) in the external drive. It is also possible copy it from the internal drive. That manual method is described by **oldfred**. See for example [this link](http://ubuntuforums.org/showthread.php?t=2147295).

When you create a fresh installed system in an external drive, you can use the instructions at [this link](https://askubuntu.com/questions/16988/how-do-i-install-ubuntu-to-a-usb-key-without-using-startup-disk-creator/942312#942312).

---

### Post by yancek on 2020-02-09
Cloning a partition to another drive obviously will not make the drive bootable but then installing Grub to the MBR and chrooting or booting it in some other manner (another OS? and running grub-mkconfig should work.  So what happens if you set the external drive to first boot option in the BIOS firmware of your computer or on another computer?  This would also require that you enable the other computer to boot in Legacy/CSM mode if it is EFI capable. Any message, errors reported?.  If you want/need EFI the link in post 2 should explain things.

> PS One a side note, when the USB drive is attached to the 'home' PC, i  cant boot into the original partition. UUID conflict? Something else? 		 

Are both the original and cloned partitions Legacy installs?  WHich has Grub in the MBR if they are?  You need to run sudo blkid to get the respective UUISs for each partition then compare them with the UUIDs you see in the correct grub.cfg and probably the /etc/fstab file.

---

