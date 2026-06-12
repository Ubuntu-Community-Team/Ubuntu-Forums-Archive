---
title: "Touchpad issues after long suspend on HP netbook"
date: 2013-05-22
forum: General Help
---

### Post by Luigi37 on 2013-05-22
Hey everyone,

On a little HP Mini 311 I have running Xubuntu 13.04 (just installed yesterday), I have some super annoying touchpad problems after suspending the laptop.  I've noticed that it only occurs if the laptop has been sleeping/in suspend for a decent while (i.e. if I put it to sleep and wake it up within maybe like 5ish minutes, everything works fine).  Everything else is functioning normally, including the left/right mouse buttons on the touchpad, the keyboard, etc.  But the touchpad is reallllly laggy or jittery.  I can furiously slide my finger across it and it only moves maybe 2 pixels (or jumps across the screen sporadically).  It seems to be acting as if a normal touchpad would when you try to use it normally but you accidentally have another finger or something resting on the touchpad as well.  

The ONLY thing that fixes the problem is to shut down the laptop.  Going back to sleep and waking doesn't work, logging out and back in doesn't work, and even turning the touchpad off and on again via terminal does nothing (the commands I've tried are "synclient touchpadoff=1" or "sudo modprobe -r psmouse").  These commands seem to turn the mouse off entirely, but when I use the commands to turn it back on it's still screwed up.

It seems that the computer has an Alps Glidepoint touchpad or something.  Perhaps that's an issue since normally touchpads are synaptics I think??

I've actually tried Linux Mint 14 with Cinnamon and then with Mate on this netbook, and those had some touchpad issues as well, albeit much worse than the current.  Any similar issues I've researched have either been inconclusive or just haven't helped me, as I can't seem to find anything exactly like what I'm experiencing.

Thanks for reading through this, hope you can help!

---

