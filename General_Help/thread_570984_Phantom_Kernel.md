---
title: "Phantom Kernel"
date: 2007-10-08
forum: General Help
---

### Post by standingfire on 2007-10-08
I have a system that was upgraded to the pre-beta of 7.10, for some reason I have four different kernels that grub does not see at all during the boot time processing. I have uninstalled this kernel in an attempt to force grub to find the other kernels and use them. It does not, in fact all of the kernels that are listed in grub at boot time are not installed on my system. 
I would like to find the files needed at boot time and examine them in order that I could change the needed files so my system will boot the way that I want it to. I am running LVM. [http://ubuntuforums.org/images/smilies/guitar.gif](http://ubuntuforums.org/images/smilies/guitar.gif)
:guitar:

Any suggestions would be most helpful.
D

---

### Post by standingfire on 2007-10-11
More information: I have evaluated this further and what I have found is there is one /boot directory that is read when the system comes up and another is displayed when the system is operational. This explains the difference between the two, now I need help is removing the /boot directory that is incorrect, for some reason the fstab not acknowledging the other partition. I am running LVM.

---

