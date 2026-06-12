---
title: "Desktop effects could not be enabled"
date: 2008-06-20
forum: General Help
---

### Post by lotrkev on 2008-06-20
I have looked everywhere all over the forums for help with this, but gotten nowhere.

I have an nivdia RIVA TNT2 Model 64/Model 64 Pro video card. I "updated it, but now it says that update is too old and it still won't work with desktop effects.

Here are my compiz-check results:

------------------------------------------------------------------------
Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         nVidia Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro] (rev 15)
 Driver in use:         nvidia
 Rendering method:      Nvidia

Checking if it's possible to run Compiz on your system...

 [COLOR="Red"]_Checking for texture_from_pixmap...               [FAIL]_[/COLOR]
[COLOR="Red"] _Checking for non power of two support...          [FAIL]_[/COLOR]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...
[COLOR="Red"][U]ERROR: NV-CONTROL extension version 1.6 is too old; the minimimum required
       version is 1.11.[/U][/COLOR]

./compiz-check: line 708: [: : integer expression expected
           [ OK ]
----------------------------------------------------------------------

---

### Post by Forlong on 2008-06-21
Sorry, your card is too old to support Compiz.

---

