---
title: "WINE on Ubuntu configuration window prob"
date: 2008-05-03
forum: General Help
---

### Post by keltranz on 2008-05-03
I am a total newbie to Linux. I have a problem with the Wine configuration window being WWAAAAYYYYYY too small or the fonts are too big.
[ATTACH]68630[/ATTACH]
I have tried uninstalling and reinstalling and restarting but to no avail. I had it working OK until I tried to reinstall using Synaptic for the updated version (not the best idea... I now see that) :confused:
Any way to resolve this??? Please help!!! Thanks!

---

### Post by ArconWan on 2008-05-03
I have not seen this particular problem with WINE before, but usually overly small or large fonts indicates that you are missing the right font and that the program is trying to use one that doesn't fit.  Typically, when I install WINE, I install the font ttf-opensymbol, but with Hardy Heron the font maintainers also added ttf-liberation which seems to compete with opensymbol.  I have both now.

I was under the impression that Open Symbol / Liberation was only used for the windows programs though, so it might not solve the issue.  I'm not an expert, so I don't know what else it could be.

Liberation is listed under the official suggested packages for WINE, which can be view through Synaptic.  Recommended and suggested packages sometimes help with random issues or add new features.  In Synaptic,  just right-click the package, and the lists are at the bottom of the context menu.

---

