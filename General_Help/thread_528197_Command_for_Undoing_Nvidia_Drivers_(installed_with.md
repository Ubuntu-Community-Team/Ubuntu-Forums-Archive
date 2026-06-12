---
title: "Command for Undoing Nvidia Drivers (installed with automatix)"
date: 2007-08-17
forum: General Help
---

### Post by Snorglorf on 2007-08-17
I read the warnings when installing Nvidia Drivers only briefly, and I cant recall the command that needs to be used in case of emergency. I think I need it, Ubuntu isnt booting. 

I should have written it down.


Its the one that uninstalls the drivers and goes back to default, any ideas?

EDIT, The precise error is as follows

Buffer IO error on device hda1, logical block 360923 (keeps repeating and counting up)

---

### Post by loserboy on 2007-08-17
i believe thats actually a hard drive error, did you have a power outage or surge?

---

### Post by Snorglorf on 2007-08-17
> **loserboy said:**
> i believe thats actually a hard drive error, did you have a power outage or surge?

Not that I know of, I wasnt the one using the computer last. My dad had it. Could this have happened from the battery running dead?


"Could not start the X server (your graphical environment) due to some internal error. Please contact your system admininisrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected"


What now? :(

EDIT: Bear in mind that i have minimal experience with linux and basically none with the command prompt

---

### Post by loserboy on 2007-08-17
> Bear in mind that i have minimal experience with linux and basically none with the command prompt

you and me both


if the battery went dead theres a chance it could have done that I guess.

is it pushing you to a command line or are you stuck in an unusable state.

edit:  did you install envy through automatix or just do the direct install of the nvidia drivers

---

### Post by w4ett on 2007-08-17
> **Snorglorf said:**
> Not that I know of, I wasnt the one using the computer last. My dad had it. Could this have happened from the battery running dead?


"Could not start the X server (your graphical environment) due to some internal error. Please contact your system admininisrator or check your syslog to diagnose. In the meantime this display will be disabled. Please restart GDM when the problem is corrected"


What now? :(

EDIT: Bear in mind that i have minimal experience with linux and basically none with the command prompt

If I'm reading correctly, after that error message you are being dumped out to a Command Line?

Looks like a reconfigure of your xorg.conf might get you back to your desktop.

from the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Select vesa as your video driver, select your resolutions, and save & close.  This Should take you back to the command line.  Type :

```
startx
```

---

