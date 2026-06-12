---
title: "Installing MacFonts?"
date: 2007-09-30
forum: General Help
---

### Post by untz on 2007-09-30
Hello there,

I am running Ubuntu 7.0.4 (through VMware Fusion) on my OS X machine...

Really am looking to install all the right fonts onto Ubuntu 7.0.4. 

Have already installed msttcorefonts but still want more aesthically pleasing fonts.

Used a program called FontExplorer (on OS X) to export all of the fonts I wanted into a zip file.

Have already transferred these fonts into Ubuntu's filesystem.

Some of these fonts are BDF fonts while others are TTF. 

How do I go about and install these fonts into Ubuntu?

Sincerely,

Unnsse

---

### Post by LPomfrey on 2007-09-30
Make sure you can view hidden files in your home folder (hit Ctrl+H) and then go into the folder .fonts (if it's not there create it now, remembering to put the "." at the start.)

Copy your fonts into here and then open a terminal and run:
```
sudo fc-cache -f -v
```

That will make it possible to use the .ttf fonts (I'm not sure about the bdf fonts as I've never tried importing any, if it doesn't work there may be a converter you can use.)

This will only make the fonts available to you though. If you want other users to be able to use them you'll need to put them in a folder in /usr/share/fonts

---

