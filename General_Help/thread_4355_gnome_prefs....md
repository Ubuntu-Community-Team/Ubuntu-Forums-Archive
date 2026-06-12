---
title: "gnome prefs..."
date: 2004-11-14
forum: General Help
---

### Post by TravisNewman on 2004-11-14
Where are the gnome prefs stored (background, panels, theme)? My gnome panels somehow got screwed up, and I logged in as root and deleted everything in /home/travis that had anything to do with gnome, metacity, panel, gtk, etc. (no, I didn't delete it all at once. I kept trying things to see if they were working). Everything. And something DID make it work again, but my theme, panel, and desktop background settings were exactly the same... so my question is, again, where are these prefs stored?

---

### Post by sfw5000 on 2004-11-14
I think most of it is stored in .gconf in your home folder. Look around in there and you'll find stuff for the desktop and other prefs. There's also .themes and .icons which store the actual themes and icons.

hth,

sam

---

### Post by TravisNewman on 2004-11-14
[QUOTE=sfw5000]I think most of it is stored in .gconf in your home folder. Look around in there and you'll find stuff for the desktop and other prefs. There's also .themes and .icons which store the actual themes and icons.

hth,

sam[/QUOTE]
 Yeah, I deleted the gconf folders as well. I kept .themes and .icons because I've downloaded a lot, but the PREFS aren't stored there are they? Those are the only ones that I kept.

This is no matter of importance, it just doesn't make sense to me.

---

### Post by sfw5000 on 2004-11-14
the settings are not stored in .themes or .icons, just the actual files. Just out of curiosity, why all the deleting of the hidden folders? If your panels get screwed up you can try the panel gui tool to fix them, or had you already tried that?

---

### Post by TravisNewman on 2004-11-14
[QUOTE=sfw5000]the settings are not stored in .themes or .icons, just the actual files. Just out of curiosity, why all the deleting of the hidden folders? If your panels get screwed up you can try the panel gui tool to fix them, or had you already tried that?[/QUOTE]
 Update: after rebooting, it finally deleted the prefs. I guess they were being held in memory or something, but rebooting fixed that, and the problems that cause the panel to screw up to begin with. And yes, I did try the panel gui

---

