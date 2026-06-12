---
title: "How can I manually adjust screensaver choice?"
date: 2007-08-02
forum: General Help
---

### Post by fred168 on 2007-08-02
Currently I have set the screensaver to "BioF" (on Feisty) which crashes the computer each time it is invoked (presumably my graphics card/driver is not up to it---but that's a different story---Dell D830). How can I reset the screensaver settings without using the screensaver gui on the preferences menu? (the gui also invokes the screensaver, as a sample, and so also crashes the machine!) 

Back in the old days we all knew where the config files were and could access them directly...

(I have tried installing xscreensaver as suggested elsewhere, but that causes crashes too)

---

### Post by mannheim on 2007-08-02
You can use gconf-editor to change the settings, or you can use the command-line tool gconftool. You need to change the keys /apps/gnome-screensaver/mode and /apps/gnome-screensaver/themes. You can change "mode" to "blank-only" or to "single" or to "random". If you choose "single", then change the "themes" key to be a list consisting of a single string such as screensavers-penrose.

---

### Post by fred168 on 2007-08-02
Super, thanks a lot!

---

