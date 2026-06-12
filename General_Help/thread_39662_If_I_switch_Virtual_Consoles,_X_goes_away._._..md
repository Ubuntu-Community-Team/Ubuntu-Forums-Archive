---
title: "If I switch Virtual Consoles, X goes away. . ."
date: 2005-06-06
forum: General Help
---

### Post by K2712 on 2005-06-06
I switched to virtual console 1 today(Ctrl+Alt+F1) and instead of seeing a prompt, I saw the end of my Xorg.0.log file:

Synaptics DeviceInit called
SynapticsCtrl called
Synaptics DeviceOn called
Warning: font renderer for ".pcf" already registered at priority 0
Warning: font renderer for ".pcf.Z" already registered at priority 0
Warning: font renderer for ".pcf.gz" already registered at priority 0
Warning: font renderer for ".snf" already registered at priority 0
Warning: font renderer for ".snf.Z" already registered at priority 0
Warning: font renderer for ".snf.gz" already registered at priority 0
Warning: font renderer for ".bdf" already registered at priority 0
Warning: font renderer for ".bdf.Z" already registered at priority 0
Warning: font renderer for ".bdf.gz" already registered at priority 0
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!
Synaptics Deviceoff called

I tried switching back to console 7(Ctrl+Alt+F7), had a blank screen with a blinking cursor in the top left corner.
So I switched back to console one, stopped X with Ctrl+C which gave me this:

waiting for x server to shut down Synaptics Deviceoff called

xinit:  unexpected signal 2

prompt:

I typed startx and x started up no problem.

I've searched the forums, wiki.x.org, and google, and I can't find anything.

Any ideas?

---

### Post by K2712 on 2005-06-07
I've been working on this for the last day, and couldn't find any solution, so out of frustration I removed my NVidia-glx driver and then re-installed it, and now I don't have that problem anymore. . .weird.

---

