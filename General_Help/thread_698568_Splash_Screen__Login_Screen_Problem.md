---
title: "Splash Screen / Login Screen Problem"
date: 2008-02-16
forum: General Help
---

### Post by pmaconi on 2008-02-16
I seem to be having a graphical problem when loading Ubuntu. After the splash screen finishes - and before the login screen appears - my monitor seems to spaz out for a few seconds. This doesn't affect performance in any way, but it is extremely annoying. 

The monitor will briefly display a bunch of brightly colored bars and what looks like a corrupted image (sometimes it says Ubuntu on the top, sometimes pieces of what my desktop looked like during my last shutdown are shown, but it is never a coherent screen). Is there any idea on how to fix this? Or even to figure out exactly what the problem is?

Thanks for the help!

[EDIT: SOLVED] Installing the new ATI driver (Feb 13th) fixed my problem completely.

---

### Post by jan quark on 2008-02-16
what is your graphic card?
what your monitor?

---

### Post by CowzRule on 2008-02-16
Basically what I believe you're seeing is the monitor being initialized or "probed" by the display drivers being loaded.
Some things you could try to fix it are:
Tweak xorg.conf
Update or Change your video card drivers.
Try a different monitor.

Good Luck :)

---

### Post by pmaconi on 2008-02-16
@jan quark
I have 2 ATI Radeon X1800 (R520) graphics cards. They are using the vesa driver. My monitor is an LG FLATRON L1932TQ - which seems to work fine, but is only detected as Plug 'n' Play - the correct model isn't listed under LG's options.

@cowzrule
What kind of xorg.conf tweaks do you suggest? I have no other monitors to try and the restricted ATI drivers slow down my system considerably.

---

