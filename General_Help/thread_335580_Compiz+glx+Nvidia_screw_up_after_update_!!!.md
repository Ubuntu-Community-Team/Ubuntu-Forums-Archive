---
title: "Compiz+glx+Nvidia screw up after update !!!"
date: 2007-01-10
forum: General Help
---

### Post by fxleytens on 2007-01-10
Hi All,

I have update my last laptop from 6.06 to 6.10, installed everything, all was OK, running perfect as well as compiz + glx with the proprietary nvidia driver (GeForce 7600) for a few weeks.

This morning, synaptic did an update of the system and now, glx does not answer anymore.

If I run glxgears, my xserver crash and come back to the GDM login. If I enable GL Desktop from the Systems-Preferences-GL Desktop, I don't have any 3d but I loose all my windows decoration.

Any idea

Thanks

---

### Post by nkkromhof on 2007-01-10
Reinstall videocard drivers, check [HERE]("http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+drivers") for steps to take.

Since you're asking for ideas, should I be sarcastic and suggest searching the forums first next time to see if anyone else has had the same problem? ;)

---

### Post by orb9220 on 2007-01-10
If you notice the upgrades had to do with restricted packages and xorg. Which anytime that happens you have to reinstall the custom binaries for your video card.

---

