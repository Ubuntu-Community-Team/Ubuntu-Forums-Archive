---
title: "How do I delete OTF fonts"
date: 2015-05-28
forum: General Help
---

### Post by ASellors on 2015-05-28
I recently installed a number of .OTF fonts using Font Viewer (double clicking font and selecting 'Install'). I've now decided that I no longer need the fonts and I'm trying to remove them. However I cannot find them either in /usr/share/fonts or /usr/local/share/fonts or ~/.fonts

Using Font Manager I can disable some of the fonts (only a couple of them, not the full set of bold and italic variations), but nowhere do I get the option to delete them permanently.

Am I looking in the right place or should I be searching elsewhere to remove the .otf files??

---

### Post by Dennis N on 2015-05-29
To delete user fonts installed by gnome font manager, use the Gear Icon on status bar > remove fonts. A pop-up window appears. Select font to be removed, then click "Delete Selected Fonts" at the bottom of the window.

Note: in gnome font manager, if the font is not in your home folder, it won't be listed for removal. 
FYI: Two possible home folder locations are ~/.fonts and ~/.local/share/fonts

---

### Post by ASellors on 2015-05-29
Excellent, the second part of your answer was just what was required. The one place I hadn't looked was ~/.local/share/fonts. A quick visit to that location showed me the fonts and I was easily able to remove them.

Thank you very much :)

---

