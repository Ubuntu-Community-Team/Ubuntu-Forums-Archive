---
title: "Unable to boot Ubuntu 16.04 because grub menu is unavailable"
date: 2018-12-06
forum: General Help
---

### Post by pkgiri23 on 2018-12-06
I am not getting grub menu after mistakenly  deleting /boot/efi directory files.So i tried to repair grub file using   both methods given in this link [https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](https://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)   . while repairing through boot repair method i get this error  ( GPT  detected. Please create a BIOS-Boot partition (>1MB, unformatted  filesystem, bios_grub flag). This can be performed via tools such as  Gparted.Then try again) . I have also created boot info summary that is
[http://paste.ubuntu.com/p/fc7GtzprS7/](http://paste.ubuntu.com/p/fc7GtzprS7/)
After that i tried second method using terminal then i get Embedding is  not possible error,blocklists are unreliable and their use is discouraged  ,grub-install will not proceed with blocklists.


 Can anyone please help me to find the root cause and how this issue can be fixed?

 Thanks,
 Piyush

---

### Post by coffeecat on 2018-12-06
Support request, not chat.

*Thread moved to **General Help**.*

---

### Post by oldfred on 2018-12-06
You have to have the ESP - efi system partition for an grub repairs to work.
> The boot of your PC is in EFI mode, but no EFI partition was detected. 
And if Boot-Repair is suggesting a bios_grub partition that is for a BIOS boot repair, not an UEFI repair.
How you boot install media UEFI or BIOS/CSM/Legacy is then how it installs or wants to repair, or always boot in UEFI boot mode. And it has to see an ESP.

Did you convert sda1 from FAT32 to ext4?
The ESP must be FAT32 with boot flag and/or esp flag.

If you convert sda1 back to an ESP, then the full uninstall/reinstall of grub in Boot-Repair's advanced mode should work.

---

### Post by pkgiri23 on 2018-12-15
Thanks [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("https://ubuntuforums.org/member.php?u=852711") it worked .

---

