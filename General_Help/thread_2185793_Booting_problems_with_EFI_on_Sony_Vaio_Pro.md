---
title: "Booting problems with EFI on Sony Vaio Pro"
date: 2013-11-04
forum: General Help
---

### Post by Sieges on 2013-11-04
Hello, 

I just got an Sony Vaio Pro 13" with Windows 8 installed. I don't want to use W8, but I would like to keep the recovery partitions just in case I change my mind.

I wiped the partition with W8 and installed Saucy Salamander. However, since this computer has EFI - it won't boot ubuntu after installation is complete.
Tried the Boot-Repair Via "Try Ubuntu" ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) but still no success. The pastebin log is here; [http://paste.ubuntu.com/6359345/](http://paste.ubuntu.com/6359345/)

Any help would be good. I am new to Ubuntu and Linux, so please treat me as such (although I am a quick learner :))

Thanks for any help!

---

### Post by oldfred on 2013-11-06
Do you get grub menu?
You still have Windows efi files shown so Boot-Repair added boot entries for that to grub. And the very newest grub has fixed the bug where it only created BIOS type entries that did not work with UEFI, so you have duplicate entries now also. Info on housecleaning in link in my signature when you get to that point.

If you get grub menu it may be video issue. What video card/chip do you have?

Often nomodeset is needed, but some newer Intel chips need other settings.
       How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by Sieges on 2013-11-08
Thanks for the reply. I managed to fix it, I don't really know how, but i changed boot mode to "Lagacy" and Ubuntu booted. I had tried that before, but all of a sudden it worked....

---

