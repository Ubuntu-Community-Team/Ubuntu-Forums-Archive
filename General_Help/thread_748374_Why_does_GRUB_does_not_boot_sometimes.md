---
title: "Why does GRUB does not boot sometimes?"
date: 2008-04-07
forum: General Help
---

### Post by FastMady123 on 2008-04-07
I got an error 17. I can't boot into Windows XP and/or Ubuntu. Why GRUB will sometimes broke?

---

### Post by diplomat.x on 2008-04-07
Try recovering Grub using any of the options listed here....
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoverGrub)

---

### Post by original_jamingrit on 2008-04-07
Hey,

according to this [grub help page]("http://users.bigpond.net.au/hermanzone/p15.htm#In_a_computer_with_more_then_one_hard") error 17 is caused by some confusion due to boot priorities, if you have GRUB installed on the master boot record (MBR) of a hard disk that is not the first.

Did you recently change the boot priorities in your BIOS menu, or change the order that your hard drives are plugged in?  If so, check you BIOS boot priorities.

---

