---
title: "MATE Desktop In Ubuntu 12.10"
date: 2012-10-22
forum: General Help
---

### Post by Rebelli0us on 2012-10-22
I [installed MATE Desktop]("http://wiki.mate-desktop.org/download?&#ubuntu_quantal_quetzal_1210_repository") but have 2 problems:

(1) It boots only occasionally, the rest of the time it says there's something wrong with graphics and goes to a black terminal screen, at which point I reset. I don't know if it's using Intel HD4000 graphics driver. How do I get this to boot reliably?

(2) How do I get rid of the floating scrollbars?

thanks

---

### Post by grahammechanical on 2012-10-22
Can you select either Ubuntu or Mate at login? Please confirm that you have the same problem when loading into a Ubuntu desktop.

Or, is this happening before you get to the login screen. Do you see a Grub menu. If so select Recovery mode. That should get you to the login using the nomodeset command. Which may get you to a desktop.

At the Grub menu you can select a kernel to boot and then press 'e' that will stop the countdown timer and bring up a screen where you can edit the boot script for that kernel entry.

You might want to remove 'quiet splash.' and then press F10 to boot that entry. Watch the messages on the screen to identify the point at which the boot process stops.

Regards.

---

### Post by Rebelli0us on 2012-10-22
> **grahammechanical said:**
> Can you select either Ubuntu or Mate at login? Please confirm that you have the same problem when loading into a Ubuntu desktop.

Or, is this happening before you get to the login screen. Do you see a Grub menu. If so select Recovery mode. That should get you to the login using the nomodeset command. Which may get you to a desktop.

At the Grub menu you can select a kernel to boot and then press 'e' that will stop the countdown timer and bring up a screen where you can edit the boot script for that kernel entry.

You might want to remove 'quiet splash.' and then press F10 to boot that entry. Watch the messages on the screen to identify the point at which the boot process stops.

Regards.

Thank you. It fails before the login. And yes after installing MATE I have the option of UIs.

Gonna reboot and see what happens...

---

### Post by Rebelli0us on 2012-10-22
I re-booted 3 times, it failed the first 2, succeeded on the 3d.

When it fails I get an error message box, "**The system is running in low graphics mode.** Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself." Then system usually is without mouse/keyboard...

---

