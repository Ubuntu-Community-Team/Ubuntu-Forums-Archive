---
title: "Ubuntu stays as a boot option"
date: 2015-04-05
forum: General Help
---

### Post by andrehsu6 on 2015-04-05
So a while ago, I dual booted ubuntu and windows, but have since uninstalled ubuntu.
But ubuntu still exists as a uefi boot option, and if you boot into that, it states something along the lines of "a minimal command terminal"
I have tried the steps listed here:
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu-uefi)
But the ubuntu boot option refuses to be removed. (Or rather it reappears)
Fix?

---

### Post by oldfred on 2015-04-06
Your link is good, but that is part 2.
You have to also delete the ubuntu folder in the efi partition first, so UEFI does not find it and add it back to the UEFI menu.
Best to fully backup efi partition, which you should do anyway.

Not sure how you mount the efi partition in Windows, but from Ubuntu live installer you can just use Nautilus file browser and open the efi partition. It may have /EFI/Boot, and will have /EFI/Windows and /EFI/ubuntu folders. Delete the /EFI/ubuntu folder. From live installer it may be mounted /media/$USER  or similar, so you have to drill down to find the folders.

Then in you can use efibootmgr to delete UEFI entries.
       # from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo apt-get install efibootmgr
sudo efibootmgr -v
ls /sys/firmware/efi/vars
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
Eamples:
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
Really UEFI boot menu edits
[http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu](http://askubuntu.com/questions/63610/how-do-i-remove-ubuntu-in-the-bios-boot-menu)

---

### Post by andrehsu6 on 2015-04-08
It worked! Thank you :)

---

