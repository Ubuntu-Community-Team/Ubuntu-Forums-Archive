---
title: "Amarok Won't Run"
date: 2008-01-09
forum: General Help
---

### Post by noper2 on 2008-01-09
I'm running Gnome on Gutsy Gibbon, and Amarok won't open anymore. It shows me the splash screen, but once it goes away, nothing happens. I can see that the processes 'amarok' and 'amarokapp' are running, but nothing seems to be happening, and the icon doesn't even appear in the notification area. Running it in the terminal I get:
 
```
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81f7d78 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x81f7d78 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

Any ideas?

---

### Post by Nimaran on 2008-01-09
Did you just install it or had it been working?

If you want you could try backing up your Amarok data folder and reinstalling it. I'm not really an expert on this kind of thing but it might be worth a try.

---

### Post by noper2 on 2008-01-09
I had it installed, and it has been working fine for months. I tried reinstalling it, but the same thing happened.

---

### Post by Nimaran on 2008-01-09
Had you recently changed any setting in Amarok or messed around with anything else on your system?

---

### Post by dlegend on 2008-01-09
You could try deleting the Amarok settings file from **.kde/share/apps/amarok**. Not sure if it would help but worth a shot.

---

### Post by noper2 on 2008-01-10
> **dlegend said:**
> You could try deleting the Amarok settings file from **.kde/share/apps/amarok**. Not sure if it would help but worth a shot.

This did the trick. I just deleted collection.db, collection_scan.files, and collection_scan.log. Thanks!

---

