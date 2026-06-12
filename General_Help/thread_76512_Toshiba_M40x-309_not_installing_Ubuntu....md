---
title: "Toshiba M40x-309 not installing Ubuntu..."
date: 2005-10-15
forum: General Help
---

### Post by OcirgamPT on 2005-10-15
I got a Toshiba M40x-309, 2GHz Centrino, M760 chipset Intel, X600SE 128MB, HD 80GB, 1GB Ram.

I boot from the CD, get the first screen for instalation ok, I pressed Enter, he starts loading drives and dooing checks them just goes blank screen and stops.

Tried using the live CD and same thing happens, then tried 5.04 live and instalation cd, then Fedora Core 4...

I got 1 partition with windows, and Unlocated partition for 10GB (intended for linux) I even tried to "hide" the windows partition so the unlocated one always came firts, but he still doesnt install, Im thinking hardware compatibility problems are causing this... But i wanted to be sure, does any1 have a similar problem? Or does any1 have a similar laptop, and can install Unbuntu in it? Iff so please help :P

Im looking for a nice Laptop for working in Ubuntu, give me some alternatives if my Toshiba is not compatible. Thank you.

---

### Post by OcirgamPT on 2005-10-15
Im sorry can an admin please move my Thread to the Instalation Help?
Sorry for beeing newbie :(

---

### Post by az on 2005-10-15
Look in the F3 or F4 options (before you press enter to boot) and see what you can do to dissable the framebuffer (vga=771) or something like that.  It sounds like a framebuffer problem.

Once you solve it, file a bug report (bug report tool, in the menu)

---

### Post by OcirgamPT on 2005-10-15
That did the trick, thks Azz, now going to a whole new level of problems, configurating wireless, sound cards, etc...
I will try to read more carefully help menu :P

---

### Post by OcirgamPT on 2005-10-15
New problem now, I got the latest X from Ubuntu 5.10, my grafics card is X600 that is suported by X, but I get an error and can load X.

m_debug_clip.o no symbols found
m_debug_norm.o no symbols found
m_debug_xform.o no symbols found
(EE) No devices detected
Fatal server error
no screens found.

---

### Post by a2ps on 2005-10-17
just change the driver from "ati" to "vesa" in /etc/X11/xorg.conf

you can try to install the fglrx driver, but chances are it wont work (X600SE still not supported for linux by ati).

---

