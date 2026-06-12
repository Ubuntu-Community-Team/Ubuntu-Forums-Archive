---
title: "grub-reboot broke grub"
date: 2007-01-09
forum: General Help
---

### Post by Demon012 on 2007-01-09
Hi guys,

I decided to try out grub-reboot to see if I could get it to reboot into windows without me being around however when I returned I found it stuck on a screen saying Error 28: Selected item cannot fit into memory

This at first I found hilarious as afterall it was booting Windows. However after I rebooted to try and start it manually it gave me the exact same error. Then I thought ah never mind I will just go back into Linux which I then tried selecting from grub.

This then gave me the error "Error 18: Selected cylinder exceeds maximum supported by BIOS"

This as you can imagine didn't go down too well.

All this caused by grub-reboot =S I don't think I'll go running to try it out again after I get this fixed.

Anyone have any idea how to fix this?? This has left me wondering what on earth is going on but I know for sure that my data is still fine as using grubs cat program I browsed the folders on the root hard disk and they seem fine.

Thanks in advance,

Demon012

---

### Post by kebes on 2007-01-09
Sounds like the bootloader itself is totally messed up. I would reinstall it.

Boot into a LiveCD, and check the file "/boot/grub/menu.lst" Make sure it is "okay" and not all screwed up. You can compare to samples files available online or post it here if you want.

Either way, you can then use the commands "grub" and/or "grub-install" to rebuild your bootloader. I think if your menu.lst is in order you can simply go:
grub-install /dev/hda

Where hda is the hard drive whose master boot record you want to install to. (Be careful! There is a big difference between /dev/hda and /dev/hda1 for instance.)


If your menu.lst is messed up, you can create a new one (back up the old one first!) by using the interactive "grub" program.


There are lots of online tutorials for grub with plenty of examples, but if you run into troubles feel free to post again... Good luck.

---

### Post by Demon012 on 2007-01-09
Ok I managed to fix the boot loader by reinstalling via a knoppix boot disk.

I did this by booting from the knoppix boot cd and then opening a terminal and using these following commands:


First I made a mount point in the ram disk 

> 
sudo mkdir /media/sda5


Then mounted the partition read write on that mount point:

> 
sudo mount -t ext3 /dev/sda5 /media/sda5


I then told used grub-reinstall telling it to redetect the drive numbers and telling it to write the new boot details to the /boot partition on sda5:

> 
sudo grub-install --recheck --root-directory=/media/sda5/ /dev/sda


Hope this helps someone else,

Demon012

---

