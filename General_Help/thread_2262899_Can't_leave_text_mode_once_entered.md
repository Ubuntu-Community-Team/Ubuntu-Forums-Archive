---
title: "Can't leave text mode once entered"
date: 2015-01-28
forum: General Help
---

### Post by xp15 on 2015-01-28
Im using Ubuntu 14.10 32bit And I want to install Nvidia  official driver as I've dome many time. But once I press Ctrl+Alt+F1, I  enter a stucked command line where I cant press anything also not  leaving back to GUI With Ctrl+Alt+F7 (or moving between F's)
  Also sometimes when I enter text mode, the splash screen appear on half of the screen.

---

### Post by xp15 on 2015-01-28
any idea? I have to insall this driver to aceive a better performance. YouTube is not playing videos good enough

---

### Post by Bashing-om on 2015-01-28
xp15; Hello;

Is the kernel intact  ? Such that we are looking at a graphics issue ?
What results when booting to terminal ?
Reboot and as soon as the bios screen clears depress and hold the right -shift- key -> grub boot menu
With the latest kernel selected press the 'e' key for edit mode -> boot parameters screen
in the parameters screen arrow down to the line starting with "linux" arrow across to "quiet splash" and replace these terms with "text" -without the quotes ;
key combo ctl+x to continue the boot process to TTY1.
Can you log into the system here ? input your username and then your pass word - there is no response to the screen when the pass word is entered, enter your pass word blindly and hit the enter key .
If this is doable
[INDENT][INDENT][INDENT]we then can look and see
[/INDENT][/INDENT][/INDENT]

---

### Post by efflandt on 2015-01-28
What nvidia card/chip do you have? That may determine which nvidia driver version to use. A very old nvidia may work with nouveau drivers, but maybe not current nvidia drivers. Or very new (like Nvidia with Maxwell chip, GTX 750, 9xx) might not work with nvidia-current, but would work with newer drivers. I don't know what version nvidia-current is in 14.10, but the 304 version in 14.04.1 was too old to support my GTX 750 Ti, but nvidia-331 worked fine.

---

### Post by xp15 on 2015-01-29
My card is an AGP NVIDIA 6200.
Currently I can't use the PC but I'll update with results. Thank.

---

