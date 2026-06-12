---
title: "amaroK Help"
date: 2007-07-19
forum: General Help
---

### Post by MarshyTheKid on 2007-07-19
Amarok will not load up for me when clicking the icon. The only way I can get it to load is with # amarokapp. 
The other night I wanted to start using amarok since Rhythmbox wasn't cutting it for me anymore. It took about 2 hours to load my 110GB library. When it was done, it started again. After that, it decided a third time would be a good idea, but I cancelled that. I had a copy of each music file in the Amarok library. Everytime I would glance away, it kept wanting to update again. It finally froze on me when I plugged in my iPod.
Here is the error report that I would get, when I tried to load it. 
```
~$ amarokapp
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80987e8 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80987e8 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
STARTUP

```
I also tried clearing my settings for Amarok, reinstalled it, completely removed it and installed it, nothing works.
Any solutions for this? I'm still a noob at Linux, but I can make do.

---

### Post by MarshyTheKid on 2007-07-20
Any help?

Its working now with the command amarokapp, but none of the global shortcuts work, and I'm not sure what the difference between the two commands are.

---

### Post by Rebeca on 2007-07-20
This might help: [http://ubuntuforums.org/showthread.php?p=2566623#postcount=4](http://ubuntuforums.org/showthread.php?p=2566623#postcount=4)

---

