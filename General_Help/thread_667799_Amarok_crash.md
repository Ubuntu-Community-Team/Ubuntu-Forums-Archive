---
title: "Amarok crash"
date: 2008-01-14
forum: General Help
---

### Post by TeraDyne on 2008-01-14
Okay, I've got a major problem. Amarok takes so long to load that it actually displays an error about it in my terminal, and when it does load, top shows it using 100%+ of my CPU. Here's what I get in the terminal:

```

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x82bbd38 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x82bbd38 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
QImage::smoothScale: Image is a null image
Amarok: [Loader] amarokapp probably crashed!

```

The "taking a long time" line comes after about a minute of no activity, and the last line occurs when I kill the app. Any suggestions?

---

### Post by Het Irv on 2008-01-14
Do any of your other KDE apps take a while to load?  It may be your KDE Desktop.

---

### Post by TeraDyne on 2008-01-14
> **Het Irv said:**
> Do any of your other KDE apps take a while to load?  It may be your KDE Desktop.

Nope. Kat, Kopete, digiKam, Kontact... they all load fine, and I have no problems using them after they've loaded.

---

### Post by hanniph on 2008-01-16
Runing amarok through **gksudo** gives me the same error.

---

### Post by mneisen on 2008-04-16
Hi, I  am running into the same problem with my Amarok. Incidentally, kaffeine has stopped working, too: it starts up all-right, but it crashes when I try to play a video file.

amarok gives me:

```
$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8150598 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8150598 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] amarokapp probably crashed!
```

kaffeine's excuse is even less: it drops dead silently. Everything used to work until two days ago. I was away yesterday, and today the problems started.

Does anybody know any solution to this? Any help is highly appreciated!

Thanks in advance!

---

