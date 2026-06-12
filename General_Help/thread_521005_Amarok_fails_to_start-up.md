---
title: "Amarok fails to start-up"
date: 2007-08-08
forum: General Help
---

### Post by RotoGrip on 2007-08-08
So i launch the app from applications/sound & video. The splash screen comes up then nothing. It shows up as "sleeping" in the processes tab. So i run amarok from the terminal and get this.

jeff@jeff-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

So then i run sudo amarok and get this output

jeff@jeff-desktop:~$ sudo amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)


Running it with sudo does work. Was working fine yesterday, get home from work today and it doesnt work anymore? Unless i sudo.

---

### Post by fredj on 2007-08-09
If you can't get it to work uninstall through the Synaptic package manager and re-install it.
When you set it up make sure that its not trying to scan for media files in any directories to
which you as an ordinary user don't have read access.

---

### Post by marko_4454 on 2007-10-20
> **RotoGrip said:**
> So i launch the app from applications/sound & video. The splash screen comes up then nothing. It shows up as "sleeping" in the processes tab. So i run amarok from the terminal and get this.

jeff@jeff-desktop:~$ amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)

So then i run sudo amarok and get this output

jeff@jeff-desktop:~$ sudo amarok
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8099220 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)


Running it with sudo does work. Was working fine yesterday, get home from work today and it doesnt work anymore? Unless i sudo.

I dont know if this has been fixed, but did you try removing the .xine folder?

```

rm -rf ~/.xine/

```

---

### Post by nlbs on 2007-10-26
Most probabbly you were using MySQL or PostgreSQl database for amarok that has been crashed fro the Current user. if you were using SQLLite may be that database has ben crashed but the database for user root is yet there in good condition. thats why its working. If somebody can tell use where is teh configuration files for amarok may be we can solve it without reinstalling.
NOTE : here is teh same problem like you and here MYSQL has been crashed and root uses SQLLite and thats why its running well for root.
Anyway : Its My debian where Amarok crashed.

---

### Post by nlbs on 2007-10-26
No Sorry the above didn't work and here is my output.```
me@host:~$ amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
me@host:~$ sudo amarok
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
Error: "/var/tmp/kdecache-neel" is owned by uid 1000 instead of uid 0.

```cant run it even as root.
Anybody plese help.

---

### Post by Yenny on 2008-01-31
I'm getting the same damn problem!

y@y-laptop:~$ sudo amarok
[sudo] password for y:
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8195158 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8195158 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QObject::connect: Incompatible sender/receiver arguments
        StarManager::ratingsColorsChanged() --> ContextBrowser::ratingOrScoreOrLabelsChanged(const QString&)
y@y-laptop:~$ kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KLauncher): ERROR: SlavePool: No communication with slave.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.
Error: "/var/tmp/kdecache-y" is owned by uid 1000 instead of uid 0.

These are the errors I've gotten just by getting it to run. It's working at the moment, but if I simply run it, it crashes. 
Is this a Gusty problem? I've uninstalled. reinstalled, I've down it with console, with synaptic-package manager... I've allowed all users rights to write and read... I don't know what else to do.

---

### Post by marko_4454 on 2008-01-31
have you tried running without the sudo? 
Why are you trying it to run using superuser?

also, you should remove /var/tmp/kdecache-y and start it up again.

I dont have much time right now, but I can help you once I get home.

---

