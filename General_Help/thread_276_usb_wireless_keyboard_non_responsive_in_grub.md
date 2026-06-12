---
title: "usb wireless keyboard non responsive in grub"
date: 2004-10-12
forum: General Help
---

### Post by hoosfoos on 2004-10-12
I have a machine that I'm dual booting win xp and ubuntu.   When i get to the screen to choose which OS to boot I am unable to choose unless I hook a ps2 keyboard up to my computer.  Once I'm past the boot screen in either OS the keyboard works fine.  The keyboard is a logitech usb wireless..

---

### Post by triad169 on 2004-10-12
This happened on my friends computer.  There was a Bios setting that needed to be changed that would enable Wireless keyboard support at boot-up.  Cant remember off the top of my head what it was but was very straight forward.  Note you will probably need to connect a ps/2 keyboard to your computer in order to access the bios.

Hope this points you in the right direction.

Triad

---

### Post by hoosfoos on 2004-10-12
It works now. There was a usb keyboard setting in the bios that was disabled, which is funny because I always enable usb keyboard support.  I must have reset the bios setting at sometime and the default is usb keyboard disabled for some reason.  Funny you can use the keyboard to get to the bios which is before grub loads with keyboard disabled.  Works now anyways :D

---

