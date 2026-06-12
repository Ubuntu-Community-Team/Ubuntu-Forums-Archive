---
title: "KDE Printing woe"
date: 2007-06-05
forum: General Help
---

### Post by PRAEst76 on 2007-06-05
Since installing Feisty I've been unable to print through KDE. Printing through Gnome seems fine, ie I can print from Firefox but not Konqueror. Problem seems to be with gs, which is invoked by the KDE printing system and then proceeds to mash my hard-drive for an indeterminate amount of time. Running it from a console it appears to be searching for fonts. I've left it doing this for about two hours then got fed up and killed it. I'm not sure where to look for information on what it is actually doing. It doesn't have a log from what I can see, or a config file (gs uses environmental variables IIRC). I've tried purging and reinstalling the kde printing system as well as cups to no avail.

Any suggestions?

---

### Post by rbmorse on 2007-06-05
If you've done kdeprint and CUPS, you might has well purge and reinstall the ghostscript packages, too, if you haven't done so already.  

Also, have you look ed at your fonts configuration in system settings?  Are they sane?

---

