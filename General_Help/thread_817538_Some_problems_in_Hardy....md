---
title: "Some problems in Hardy..."
date: 2008-06-03
forum: General Help
---

### Post by Old Marcus on 2008-06-03
Well, upgraded to hardy recently and I have to say, it hasn't really impressed me that much. I may do a clean install, but I'll see if I can get these fixed without a reinstall.

Firstly, and most noticeably, there are no loading splash screens whatsoever. Ubuntu still loads up fine, but no splash screen.
Next, on the login screen, part of it is chopped off on the bottom, leaving it looking crude and messy.
Also, I get these weird black strip/dot things along the top of my screen, and I know it's nothing to do with my monitor, seems to be graphical glitch.
Also, second most noticeable thing, quality of sound when playing music has dropped a lot. tracks not consistently stutter and listening to music becomes unbearable. I understand a new version of pulseaudio was installed? Could this be the problem?

If anyone could help with any of these problems it would be much appreciated. Thanks. :)

---

### Post by EXCiD3 on 2008-06-03
1) Check to see if "splash" is in the boot entry in grub.
As for the rest its probably way easier for you to just reinstall. I've tried to help with several issues related to graphics and every time we spent hours and only made it to the conclusion we should have just reinstalled.

---

### Post by Old Marcus on 2008-06-03
Well, I seem to have fixed the sound issue by using Amarok. how do I sheck if splash is in the boot entry?

---

### Post by EXCiD3 on 2008-06-03
Open /boot/grub/menu.lst and look through the entires at the bottom of the file.

---

