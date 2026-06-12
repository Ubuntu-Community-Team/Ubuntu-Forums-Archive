---
title: "I need to set the consoles to 80x24"
date: 2017-08-09
forum: General Help
---

### Post by mtmigs on 2017-08-09
I have a text application that uses a standard 80x24 character display. I would like to use the console display to run the program (no gui). The current console is much bigger than 80x24 making it very difficult to read the program's screen. I need 80x24 on the consoles. I tried setting GRUB_GFXMODE=640x480 but even after update-grub and reboot nothing changed.

---

### Post by JKyleOKC on 2017-08-11
The setting for grub that you made will affect only the grub screens themselves. It'll require other settings to affect what happens after the boot process completes. Unfortunately, those settings will be very dependent on your system's hardware, especially on the video card and its driver. You'll have to tell us more about the hardware and software -- we need to know the brand of video adapter the machine uses, and anything you can discover via the command "lshw" as well.

---

### Post by mtmigs on 2017-08-15
Researching a different computer's problem what I need is to disable gfx mode and I will have what I want.

---

