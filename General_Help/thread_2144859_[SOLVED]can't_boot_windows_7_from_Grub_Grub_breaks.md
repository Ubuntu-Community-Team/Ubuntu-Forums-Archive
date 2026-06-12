---
title: "[SOLVED]can't boot windows 7 from Grub /Grub breaks windows 7 boot"
date: 2013-05-13
forum: General Help
---

### Post by petermg on 2013-05-13
I have Windows 7 and Ubuntu 13.04 installed on the same drive.  At some point I was unable to boot into Windows 7 even though it was listed in the grub boot menu.  When I would select it, the screen would go blank for a moment, then the computer would reboot and eventually grub would come back up.  Only Ubuntu would boot.  I was able to get back into windows 7 by booting off the windows 7 DVD, going to REPAIR COMPUTER, command prompt then "bootrec.exe /fixboot" and "bootrec.exe /fixmbr".  These got me back into windows 7 but now I don't have grub.  I tried the app Boot Repair in Ubuntu, and it said it worked, and grub did come back, however it had the exact same problem.  I was unable to load windows 7 even though it was listed in the boot menu.  It would do the same thing as before, it would go blank for a moment, then POST would show and start all over again going into grub, so basically if I try to boot into windows 7 the system goes into a boot loop unless I select Ubuntu.  Maybe the app BOOT REPAIR isn't the route I should take in this situation?  I've used it successfully on other PCs, but for some reason it's not working on this one.  Any help is greatly appreciated.  Currently I'm without any Grub and I can boot into Ubuntu using the SuperGrub CD otherwise my system just goes straight into Windows 7.  Thanks again for any replies!  Another note, when I had BOOT REPAIR install Grub although was not able to boot into Windows 7 from it, even though it showed up in the menu, I tried the SuperGrub CD to boot into windows7 and it gave me the SAME BEHAVIOR as loading it from the Grub boot menu, it would just go blank for a moment then the PC would reboot.  Seems like grub is damaging something that windows 7 needs to boot up, and the only way I have thus far been able to get back into windows 7 is doing the bootrec.exe commands I listed above.  So I am wondernig if I'm not going to be able to do dual boot on this PC for some reason?  I've never run into this issue before.

---

### Post by oldfred on 2013-05-13
Are you hibernating in Windows?
Or maybe Windows needs chkdsk? I had something similar with XP, where it worked on its own but from LInux could not be seen. After chkdsk it worked better in XP.

---

### Post by Mark Phelps on 2013-05-13
Sound like what Boot-Repair is doing is installing GRUB to the Windows boot partition -- which will work for Ubuntu, but prevent Windows from booting.

As an alternative, suggest you look into using EasyBCD.  The NeoSmart Technology forums provide this for free, you install it in MS Windows, and then you can use it to boot into Ubuntu.

---

### Post by petermg on 2013-05-13
oldfred, I'm not hibernating and I ran chkdsk and it found no errors and it didn't resolve the issue.

Mark, EasyBCD worked great!  Thanks for the info.

---

