---
title: "Amarok and Katapult issue(s)"
date: 2007-08-06
forum: General Help
---

### Post by kidamnesiac on 2007-08-06
Running Edgy Kubuntu, mostly flawlessly except for the last month or so when the following issues arose:

I can't start amarok from the K(start)-menu, or command line. When typing in amarok into the command line, I get the long blank stare of a cursor and nothing happening for infinitety. When starting from the K-menu, I get the bouncing cursor and the ghost of the amarok application appears in the application panel (the thing across the bottom), but then does not start. When I type amarokapp into the command line, I get this:

kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099eb8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099eb8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP


and it starts fine. I have tried deleting the config and app files from the .kde menu and purged more times than a bulemic but no dice. Any suggestions?

Also, katapult does not work either. Not from command line or k-menu. I really like katapult! 

This started after nothing in particular, just some package upgrades. Running an old athlon 1600+ box.

Any suggestions would be graciously appreciated with e-milk-and-cookies.

---

### Post by ChameleonDave on 2008-03-25
It's a bit of a lame solution, but have you tried simply reinstalling Amarok and Katapult?

Also, see [http://ubuntuforums.org/showthread.php?t=115947](http://ubuntuforums.org/showthread.php?t=115947)

---

