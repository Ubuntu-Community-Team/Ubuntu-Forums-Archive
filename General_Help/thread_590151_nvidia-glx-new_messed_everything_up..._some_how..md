---
title: "nvidia-glx-new messed everything up... some how."
date: 2007-10-24
forum: General Help
---

### Post by Dracojk on 2007-10-24
Some how when I tried to enable nvidia-glx-new, it caused my xorg.conf settings to reset, or something bad happened.  When I restarted the computer, it said it had to load low graphics mode.

Even when I go back and disable nvidia-glx-new, and try to install nvidia-glx, there is no change.

Before trying to do this, compiz worked fine, and everything was great, except a small error message saying glx was not working, which is what prompted my trying to turn it on.

The error didn't seem to do much, except cause compiz to unload when I closed the terminal window.  If I leave the window open, everything runs smoothly, as far as I can tell.

How can I get my xorg to go back to what it was before?  I tried using cp to switch it out for the xorg.conf.backup file that was in the folder, but that didn't help at all.

Ideas?:confused::confused:

[edit]

Oh, I'm running this on a Dell i9300, with an nVidia GeForce go 6800.

---

### Post by rjpilla on 2007-10-24
Yeh i had the same problem. Just go into the xorg.conf file and change the word nvidia to nv in the device section. Only problem is your not actually using the nvidia driver so you will have no 3d which i need. Haven't found the answer to this problem yet. I'm using a GeForce 5700 128 mb. If you have further info on this let me know. I've tried Envy also no luck.

---

