---
title: "VC4 on Raspberry Pi Zero 2 W"
date: 2023-01-25
forum: General Help
---

### Post by ctradoumis on 2023-01-25
I’m wondering if someone has an answer or at least can point me in the right direction. 

I am running a RPI Zero 2 with Ubuntu 22.04 64 but and regardless of the combination of config.txt settings, fkms, kms, cma and so on. No change

Dmesg and lsmod have no reference to VC4 or drm
/dev/dri does not exist
It seems the Roi 4 B dtb is being used but I can’t confirm.
I can manually load the VC4 and drm modules but still no /dev/dri

I’m lost at this point as this all works in 32 but, but unfortunately I need 64



Any help here would be greatly appreciated. 

Thank you.

---

### Post by ctradoumis on 2023-01-26
Edit: I am able to get what I need when manually loading the dtoverlay vc4-kms-v3d after full boot. But I’m getting mixed results when adding the line to config.txt.

If I add it at the top with the [all] kernel and such lines, I get full boot but no modules

If I add it to the very bottom below [all]
I get a black screen and no full boot. No networking comes up. 

Still very strange.

---

### Post by HermanAB on 2023-01-27
There are three or four things called VC4…

---

### Post by ctradoumis on 2023-01-28
Which does dtoverlay vc4-kms-v3d refer to? The question is, with context to /dev/dri - referring to video so the other 2-3 things called VC4 are not within context. Thanks for pointing it out though. Quality reply for sure.

---

