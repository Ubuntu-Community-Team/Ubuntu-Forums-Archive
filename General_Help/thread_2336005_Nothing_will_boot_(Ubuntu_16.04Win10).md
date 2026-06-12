---
title: "Nothing will boot (Ubuntu 16.04/Win10)"
date: 2016-09-03
forum: General Help
---

### Post by Stilian_Zagorov on 2016-09-03
Info: 
PC: Acer Aspire E5 
Processor: AMD A6 64bit
RAM: 8GB

Hello, I installed Ubuntu 16.04 on a UEFI alongside preinstalled Windows 10 (also UEFI). I used boot-repair to fix GRUB, but it didn't work.
It told me to run the following command in administrator CMD:
"bcdedit /set {bootmgr} path \EFI\ubuntu\shimx.64"
Now Windows Boot Manager is gone from the BIOS boot menu and I can't boot into Windows. I assume boot-repair was only for Windows 7, but it's too late now. When I enter boot manager (spamming F12 before boot), there are no boot devices listed. 

Any help is appreciated. I'm so upset right now <_<.
Thanks

Edit: just fyi:
When I turn on the laptop, it says "No Bootable Device" and shows a hard drive with a magnifying glass on top.

---

### Post by Stilian_Zagorov on 2016-09-03
After 15 minutes of googling for help while crying, I found an article that worked. I simply needed to enter the bios and do some stuff there. Thank you if you already started looking for a solution. I can finally say (after 6 months of trying to do this) that my laptop has both Windows 10 and Ubuntu 16.0 4, and that none of them are I'm any way messed up.

---

### Post by Delupara on 2016-09-03
6 months jesus 0_o???

---

### Post by Stilian_Zagorov on 2016-09-03
Yeah -_-. I got the laptop in December, and a few months later Windows started messing up. It has been about 6 months since I decided to dual boot Win10 and Ubuntu, but because of the unavailability of USB flash drives, and my laziness, it took me this long. I have tried over a dozen times, for sure, though.

---

