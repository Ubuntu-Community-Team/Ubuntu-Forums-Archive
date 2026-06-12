---
title: "Install and uninstall"
date: 2007-10-20
forum: General Help
---

### Post by vegetosayajin on 2007-10-20
I have a question 
After all is said and done how can I uninstall Ubuntu without having the error that I got the last time that I tried this.It said something like unable to load grub...and other  stuff that I truly don't understand yet
so how can I entirely erase the partition and the grub manager that loads ubuntu and windows dualboot on my computer when I decide to do so:confused:


PS:and another question :how can I set the default load to be windows-
for info I'm running **Windows XP and Ubuntu 7.04 feisty fawn**

---

### Post by jespdj on 2007-10-20
GRUB is the boot loader - a small program that loads when your computer starts up, before the operating system is loaded.

If you have multiple operating systems installed on your computer, for example Ubuntu and Windows, GRUB will display a menu for a few seconds when you start up the computer where you can choose which OS you want to start.

If you have both Windows and Ubuntu on your computer and you want to remove Ubuntu and GRUB, then you can do that with the Windows recovery console. You get to the recovery console by booting from your Windows XP CD or and pressing "R" at one of the first screens. In the recovery console, you can type the command "fixmbr" to restore the Master Boot Record back to the original Windows boot loader.

More info: [Description of the Windows XP Recovery Console (Microsoft)](http://support.microsoft.com/kb/314058)

---

### Post by vegetosayajin on 2007-10-20
> **jespdj said:**
>  You get to the recovery console by booting from your Windows XP CD or and pressing "R" at one of the first screens. In the recovery console, you can type the command "fixmbr" to restore the Master Boot Record back to the original Windows boot loader.

More info: [Description of the Windows XP Recovery Console (Microsoft)](http://support.microsoft.com/kb/314058)
And if I just Delete the two partitions-swap and the main linux part-or I just have to do it the way you told me:confused:

---

### Post by -Zeus- on 2007-10-20
You can't just delete the partitions... you need to rester the MBR to original THEN remove the partitions.  If you just remove them, the GRUB won't load and you will end up with a nice paperweight :-D

---

