---
title: "Need to reboot every day"
date: 2007-08-07
forum: General Help
---

### Post by ChasHutch on 2007-08-07
I am running Feisty on an HP Pavilion PC.  Everything is great and I am happy with how things are set up and am using this as my daily desktop PC.

My issue is that when I leave the PC running overnight, I have to reboot because it is completely locks up when I go to use it in the morning.

I have shut off all of the power management settings in the PC BIOS and have turned off all the settings that I can find relating to power-save and power-management in Gnome.

Here's what I can tell you:  the num lock and the caps like lights on the keyboard are flashing on and off and the keyboard and mouse are NOT functioning.  Since I can not mouse or keyboard, I can not reboot or get to a command prompt.  I also can not Ctrl-Alt-Backspace to get out of gnome.

Thoughts, ideas?  :?


Thanks,

---

### Post by psusi on 2007-08-07
Run memtest86 on the livecd?

---

### Post by ChasHutch on 2007-08-07
No.  So, boot from the live CD and run memtest86. ??

---

### Post by RedSquirrel on 2007-08-07
If you can get the machine to work upon reboot, you should be able to select the memtest from the grub menu. The flashing LEDs indicate a kernel panic.

EDIT:

kernel panic: possibly caused by bad h/w somewhere or sometimes the kernel itself not being the best one for the tasks you are doing... I assume you're using the standard generic kernel which should be OK for most things. You're not running a custom kernel or the server kernel, are you?

---

