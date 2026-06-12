---
title: "[SOLVED] Amarok not loading... (used to?)"
date: 2008-03-10
forum: General Help
---

### Post by mrfraser89 on 2008-03-10
I'm running 7.10 64 bit, and it's updated fully.

Amarok has some issue starting up (not after anything in particular happened to the system though).

Running from terminal outputs this.

Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Error: "/tmp/ksocket-fraser" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-fraser" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-fraser" is owned by uid 1000 instead of uid 0.
kbuildsycoca running...
Error: "/var/tmp/kdecache-fraser" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-fraser" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-fraser" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-fraser" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-fraser" is owned by uid 1000 instead of uid 0.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x85a800 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x85a800 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
Error: "/tmp/kde-fraser" is owned by uid 1000 instead of uid 0.


Any ideas?

---

### Post by NightwishFan on 2008-03-10
EDIT: uncalled for

Try to completely remove amarok in synaptic. Then open a terminal and run:
sudo apt-get update
sudo apt-get install amarok

---

### Post by mrfraser89 on 2008-03-10
No luck, the issue seems to be that even after a reinstallation (through synaptic, through terminal, any of the options) the configuration hasn't changed.

Eg, no new setup for amarok or anything, it's just loading the previous configuration which seemingly is causing trouble.

---

### Post by NightwishFan on 2008-03-10
ok now i got it uninstall amarok and then try to delete its config file in mine its located at:
/home/username/.kde/share/apps/

then reinstall and it should remake the folder on its own.

---

### Post by forestpixie on 2008-03-10
delete the config folder in your home - open nautilus and view hidden files

go to /home/*yourname*/.kde/share/apps

and copy the amarok folder somewhere else - then try reinstalling

---

### Post by mrfraser89 on 2008-03-10
SUCCESS :D!

Now to not stuff it up again :)

Thanks greatly for your help mate, made me happy late on a Monday night :)

---

### Post by forestpixie on 2008-03-10
best time to be happy - or is that Friday night - can you mark thread as solved :D

Wouldn't have posted if I knew that NightswishFan's "Edit" was turning into the same as I posted

---

### Post by NightwishFan on 2008-03-10
:KS:popcorn::KS We own.

---

