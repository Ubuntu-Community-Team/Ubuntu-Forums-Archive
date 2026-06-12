---
title: "remove ubuntu"
date: 2008-01-03
forum: General Help
---

### Post by animetauren on 2008-01-03
i just installed ubuntu on a removable harddrive now when i boot my computer it says grub errror 21 and i can only boot from the ubuntu hard drive how do i remove ubuntu and set things back to to normal and my xp was preloaded into my computer so i don't have no installation cd to boot from please help

---

### Post by gazj on 2008-01-03
use a windows cd, does not have to be xp, boot from the windows cd

for windows 2000 and XP cd's

press R when asked to enter the recovery console then enter the following commands

fixmbr
fixboot

or windows 95,98,me cd's when you get to the command prompt type the following comand

fdisk /mbr

this will reinstate the windows boot record that was replaced by ubuntu, windows will carry on as it was.

---

### Post by gazj on 2008-01-03
just see the cd bit

download a windows98 floppy from [www.bootdisk.com](www.bootdisk.com) and create a floppy bootdisk

then follow the windows98 cd instructions above

---

