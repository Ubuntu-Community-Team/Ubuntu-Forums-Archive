---
title: "Amarok won't load, other apps freeze"
date: 2007-11-01
forum: General Help
---

### Post by Black_Monkey on 2007-11-01
Whenever I try to run Amarok, it won't load (running from the command line outputs nothing), and other apps which are connected to Amarok (e.g. Katapult, Kopete when the Now Playing plugin is loaded) freeze up until I do a *kill amarokapp*. I just put a music CD in, and my system became completely unresponsive. I rebooted the PC, and I'm still having the same problem. Does anyone have any ideas?

Edit: About 15 minutes after trying to open Amarok, it's just started... sort of. It's looking like this: [[IMG]http://img404.imageshack.us/img404/8360/amarokbb7.th.png[/IMG]](http://img404.imageshack.us/my.php?image=amarokbb7.png)

Edit2: After running it from the command line, after about 15 minutes it loaded and it said:
```
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8141da8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8141da8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

```

---

### Post by Jhereg on 2007-11-01
I, too have just recently began getting a similar problem.

I think (for me at least) the problem may have something to do with trying to play files converted with sondkonverter. I just recently converted my entire media library from wma to .mp3 so i could use it on my windows computer, linux computer, and music phone. Amarok only froze the first time i tried to play these files, now it will never load.

this is the console output trying to run amarok.
```
jacob@Jacob-Kubuntu:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099f18 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099f18 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?

```

---

### Post by Black_Monkey on 2007-11-02
Ah, I found out that if I wait even longer it eventually loads up properly, and going to "Rescan Database" solved the problem - hopefully that will work for you too Jhereg

---

### Post by Jhereg on 2007-11-07
Thanks for the suggestion. For some reason, the problem appears to have fixed itself.

Thanks anyway.

---

