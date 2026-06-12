---
title: "I messed up bad with gnu grub"
date: 2014-10-12
forum: General Help
---

### Post by Hannan_Rhodes on 2014-10-12
i had Ubuntu installed duel booting with windows. One day the partition with ubuntu was formatted and I couldn't recover it. So the problem is ever time i boot up it goes through 3 stages of gnu grub recovery.  For example i boot up and gnu grub recover comes up, i exit, another gnu grub recover pops up i exit and  when i exit the 3rd one then it finally boots into windows. Because of this i cant boot into a cd or usb. Some one help.

---

### Post by yancek on 2014-10-12
Which windows version are you using?
If you are getting a Grub boot, then you are booting from the hard drive.  You need to change the settings in the BIOS to put the CD drive or flash drive as first in boot priority.

---

### Post by Hannan_Rhodes on 2014-10-12
im using windows 8. But i cant get into bios because when i boot up the first thing that loads is gnu grub.

---

### Post by yancek on 2014-10-12
Are you using GPT/UEFI with windows?  Was windows 8 pre-installed?  Did you install Ubuntu as GPT/UEFI?  You might need to download the bootinfoscript or boot-repair script and run that from your Ubuntu installation medium.  Grub can't be accessed before the BIOS and is it always on the hard drive.  What type (manufacturer) of computer is it?

---

