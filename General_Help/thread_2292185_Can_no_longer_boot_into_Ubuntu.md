---
title: "Can no longer boot into Ubuntu"
date: 2015-08-25
forum: General Help
---

### Post by dan191 on 2015-08-25
I have set up a dual-boot system with Ubuntu 14.04 and Windows 8, which had been working well for a few months, but after a recent series of updates to Windows I can no longer boot into Ubuntu. I tried using Boot Repair to fix the problem, but it doesn't seem to have worked. The log from Boot Repair is at [paste.ubuntu.com/12193170]("http://paste.ubuntu.com/12193170") .  I'm not sure what to do from here, so any advice is appreciated.

---

### Post by oldfred on 2015-08-26
Where are all the duplicates of your ubuntu boot files coming from?

You should only have one of these:
/EFI/ubuntu/MokManager.efi
/EFI/ubuntu/grubx64.efi
/EFI/ubuntu/shimx64.efi 

The last entry of 
sudo efibootmgr -v
shows an ubuntu entry now.
Can you boot that from one time boot key like f10 or f12, but varies by brand.

I would house clean out all the duplicates.

You may also want to reduce the number of kernels.

Check current kernel I also keep one older just in case:
#Current kernel:
uname -a
prefer synatic and keeping 2 kernels, current and one known working older on.[URL="http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu"]
http://askubuntu.com/questions/2793/how-do-i-remove-or-hide-old-kernel-versions-to-clean-up-the-boot-menu[/URL]

---

