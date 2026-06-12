---
title: "Booting problems"
date: 2019-10-26
forum: General Help
---

### Post by joshua-powers22 on 2019-10-26
I installed Ubuntu 19.10 on an external usb 3 hard drive 1tb, during live boot and I think the first native reboot for updates the boot screen was fine and beautiful but now is a low res crappy version stuck one one side (as opposed to filling the screens) the only thing I did between the normal boot and this one was use grub customizer to set windows to boot by default and reduced the timer from 10 to 5 secs. also speaking of grub, sometimes (not every time) I get a grub rescue screen where I need to type exit to get to the normal grub screen, be advised I had ubuntu on this machine years ago and could never get rid of that ubuntu uefi entry in the setup screen (bios) and now this ubuntu install seems to have taken that entry over (as there are no other ubuntu entries in uefi) I'm no stranger to linux but it has been awhile

---

### Post by yancek on 2019-10-26
Is the Ubuntu install on the external hard drive on a GPT drive?  Did you do an EFI install of Ubuntu?  Are the Ubuntu EFI files for boot on the internal drive on a FAT32 partition or did you create a FAT32 partition on the external drive for your Ubuntu EFI files?.

Might be best to get the boot repair software from the site below and run it with the Create BootINfo Summary option and NOT try to make any repairs.  YOu should get a link when it finishes and you can post it here for members to review and make suggestions.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by joshua-powers22 on 2019-10-26
not on a gpt drive efi install but I didn't make a efi partition, I told the installer to install to that drive but I guess it defaulted to the efi partion on the main windows ssd

---

