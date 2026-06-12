---
title: "problems installing Edubuntu: Turning on gate A20"
date: 2007-11-15
forum: General Help
---

### Post by barto on 2007-11-15
Hi,

I have tried to install Edubuntu 7.10 desktop i386 using wubi 7.10rev386, but when it does the first reboot it hangs displaying 
Booting GRLDR...
Turning on gate A20...
The cursor is flashing at the end of the gate a20 line.

I have not found any similar bug report in the forums, but maybe it is a know problem.

Is there any error logs (or similar) I can provide to help identify and solve this problem?

By the way, the computer has a Intel 82865G graphic card. The LiveCD seems to dislike this graphic card, but it is possible to get the LiveCD running if I press Alt+Ctrl+F1 at the beginning of the boot process of the LiveCD.

Thanking you in advance,
Barto

PS: I have tried Wubi in other computers and it worked OK. Congratulations for this good work!

---

### Post by ago on 2007-11-15
Send a PM to tinybit and bean123 they are the grub4dos masters

---

### Post by tinybit on 2007-11-16
A20 gate is a known problem. Thanks for the report.

In the coming grub4dos 0.4.4, we will try to solve this problem.

Testers are welcome. Please pay attension to the possible releases labelled grub4dos-0.4.4pre* or 0.4.4-2007-xx-xx. The main download site is [http://download.gna.org/grub4dos/](http://download.gna.org/grub4dos/)

---

### Post by SilentJoe on 2007-11-17
Must be my bad luck.  I downloaded Xubuntu today, loaded up the live CD, wiped my XP and installed.  Rebooted and BOOM.  I have teh Gate A20 problem.

Guess I'll just live with the live CD until its fixed.

Oh joy.

- SJ

---

