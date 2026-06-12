---
title: "[SOLVED] Grub boot editing..."
date: 2008-07-10
forum: General Help
---

### Post by TommyGun1 on 2008-07-10
Hello,
I want to delete some items from the boot loader (when the pc starts the bootloader shows a list of operating systems), there are many Ubuntu versions and recovery modes on the list, I want to get rid of those and just leave the latest version Ubuntu and recovery mode for it. Also I want to install BackTrack 3. Thanks

---

### Post by lisati on 2008-07-10
The relevant file is /boot/grub/menu.lst, which can be edited with ```
gksudo gedit /boot/grub/menu.lst
``` Don't forget to enter ```
sudo update-grub
``` when you have made your changes.
I'd suggest commenting out the part you don't want to show at boot-up by putting "#" at the start of the line for the time being, just in case something goes wrong and you need to go back a version or two. Later, when you are happy with how things are going, you can look at cleaning out your system.

---

### Post by Bigtime_Scrub on 2008-07-10
I don't know if editing the boot loader is even possible but I do have a link for BackTrack3 that might help you. I've never actually done that install myself but if you follow along it shouldn't be too problematic.

[http://www.beyondthebit.com/node/17](http://www.beyondthebit.com/node/17)

---

### Post by drs305 on 2008-07-10
The easiest and safest way for new users to edit the grub options is to install and use StartUp-Manager - a gui-based grub editor. You can select how many kernels to view, how long to display the menu, which OS or kernel to use, what basic colors or background to display, and much more.

To install StartUp-Manager:
```
sudo aptitude install startupmanager
```

To use:
System, Administration, StartUp-Manager

In the tutorial section, here is a explanation of the options and how to edit the menu.lst either with SUM or manually:
[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by TommyGun1 on 2008-07-10
Thanks it worked :)

---

### Post by Gunman1982 on 2008-07-10
Instead of updatint the menu I would just remove the old kernel images via synaptic. Now they are still on the system and you just don't see them in the menu. If you remove them via synaptic the entry in the grub menu will be rmoved too. Just watch out not to remove the latest kernel.

---

