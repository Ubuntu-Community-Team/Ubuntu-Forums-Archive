---
title: "What have i done wrong? only 1-4fps in WoW"
date: 2007-10-13
forum: General Help
---

### Post by noobi on 2007-10-13
I have now googled and posted on forums for weeks - but i can not find a solution to my problem. So i really hope that someone here can help me?

Everything in wow works except that i only have 1-4fps - so it is impossible to play. What have i done wrong? or is there something i have forgotten to do?

It would really be sad if i have to go back to windows because of that :(

--------------------------------------------------------------------------------------------------------------------------------

This is what i have done:
1. Installed Ubuntu 7.04.
2. Installed all the updates for Ubuntu.
3. Installed the ATI driver with this guide=http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide.
4. Installed WoW and the expansion with Wine.
5. Updated it with all the patches.
6. Added to xorg.conf (before that it would freeze after playing >still with only 1fps< for 3min.) =
Option "Capabilities" "0x00000800"
Option "UseFastTLS" "off"
Option "KernelModuleParm" "locked-userpages=0"
7. Added to regedit = a key named "OpenGL" under HKEY_CURRENT_USER>Software>Wine and a string value called "DisabledExtensions" (someone told me it would give me more fps - but it did not work).
8. Added to config.wtf =
SET gxApi "opengl"
SET ffxDeath "0"
SET ffxGlow "0"

I use Ubuntu and wine.
My PC:
Packard Bell EasyNote MX
Intel dual-core 1.7ghz
ATI radeon x200
1024mb ddr2
140gb hd (i think)

---

### Post by pay on 2007-10-13
Post the results from ```
fglrxinfro
``` to make sure that the driver installed correctly.

---

### Post by noobi on 2007-10-14
It says:

tobias@tobias-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON XPRESS Series
OpenGL version string: 2.0.6334 (8.34.8 )

Warcraft 3 ft works fine..

---

### Post by pay on 2007-10-14
Try ```
nice -15 wine wow.exe

```

---

### Post by noobi on 2007-10-16
that did not help :(

---

