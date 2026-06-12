---
title: "Blank desktop with Nvidia driver"
date: 2014-10-29
forum: General Help
---

### Post by canadianwriterman on 2014-10-29
I recently installed 14.04 on my HP desktop with an Nvidia graphics card. The install went fine, but then booted to the Ubuntu desktop with no icons or mouse. Figuring it was a graphics driver problem, I rebooted into the low graphics mode using recovery mode and checked the alternate drivers. Nouveau was the default driver, so I switched it to the "tested" Nvidia driver (I didn't make note of it, but it ended with 331). Unfortunately, it didn't make a difference and I still had no icons or mouse.

Now when I boot using recovery mode, the machine will not boot into the low graphics mode so that I can try a different driver. I am stuck with an Ubuntu desktop with no icons or mouse. Any suggestions how I can get into the system to try a different driver? And, I guess a better question is: how do I know which Nvidia driver to choose? Thanks for your help.

---

### Post by Frogs Hair on 2014-10-29
If you are getting a right click context menu on the desktop you can select change desktop background and navigate from Appearance to All Settings > Software & Updates > Additional Drivers. From there you can revert to the  [COLOR=#000000]Nouveau driver or test another. 

[/COLOR]Alternatively, installing and removing software is possible from TTY (Ctrl + ALT +F1) (Ctrl + Alt + F7) returns to the desktop. If using TTY the complete package names are required and I can't supply the names because I'm using 14.10 so the available driver versions may be different.

---

