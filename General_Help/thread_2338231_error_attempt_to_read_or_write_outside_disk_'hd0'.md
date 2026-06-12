---
title: "error: attempt to read or write outside disk 'hd0'"
date: 2016-09-26
forum: General Help
---

### Post by lumaja2 on 2016-09-26
Ubuntu 16.04 LTS installed on Seagate 500GB hard drive, I think it was after an upgrade that this error shown, it happens some times not always when I boot the computer in the morning then I restart the computer and the Grub screen comes up counting seconds when it finishes another full screen comes with &#8220;(numbers) at1:00 status [DRY]&#8221; eventual it reboots, have no effects during the working session but when Shut down it takes very log time to shut.
 Never had this error with previous Ubuntu OS.
 Please help me to fix this problem

---

### Post by oldos2er on 2016-09-26
Have you run [smartctl]("https://help.ubuntu.com/community/Smartmontools") on the drive? If you have more than one kernel installed, try booting them to see if the DRY errors are still present.

---

