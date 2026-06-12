---
title: "Audio players not working"
date: 2007-04-10
forum: General Help
---

### Post by DougieFresh4U on 2007-04-10
No matter which audio/media player I open, it freezes. They worked ok this morning. But tonight, I open, let's say Exaile and then it freezes and I click to close it and force quit pops up. how can I find out what is causing this? Thanks for any help

---

### Post by haricharan on 2007-04-10
try opening them from terminal and post the output that you get....someone wud be able to help you....

---

### Post by DougieFresh4U on 2007-04-10
> **haricharan said:**
> try opening them from terminal and post the output that you get....someone wud be able to help you....

Thanks, here ya go:;:~[B]$ exaile
/usr/share/exaile/xl/xlmisc.py:42: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon
/usr/lib/python2.5/site-packages/mutagen/m4a.py:41: DeprecationWarning: mutagen.m4a is deprecated; use mutagen.mp4 instead.
  "mutagen.m4a is deprecated; use mutagen.mp4 instead.", DeprecationWarning)
Error grabbing key 162, 0x849b018
Plugins 'Alarm Clock' version '0.1' loaded successfully
Plugins 'Desktop Cover' version '0.1' loaded successfully
Plugins 'LibNotify Plugin' version '0.1' loaded successfully
Plugins 'Mini Mode' version '0.1' loaded successfully
Plugins 'Serpentine Plugin' version '0.1' loaded successfully
Plugins 'Streamripper!' version '0.1' loaded successfully
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x86bef20>}
mmkeys are available.
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
Importing /home/dougie/.exaile/saved/playlist0000.m3u[/B]and here::[B]~$ amarok

X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Amarok: [Loader] Starting amarokapp..
Amarok: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DCOPClient::attachInternal. Attach failed Could not open network socket
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
kbuildsycoca running...
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8137040 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8137040 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2c0003e
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
Amarok: [Loader] amarokapp probably crashed![/B]
)

---

### Post by DougieFresh4U on 2007-04-10
bump

---

### Post by taurus on 2007-04-10
Does it freeze if you use another audio or media player like xmms or mplayer?

---

### Post by DougieFresh4U on 2007-04-10
> **taurus said:**
> Does it freeze if you use another audio or media player like xmms or mplayer?

all media players freeze. I can play youtube and games even games using wine and sounds work in games and system

---

### Post by taurus on 2007-04-10
And you said you have Edgy on your machine.  Is that the old Celeron PC?

---

### Post by DougieFresh4U on 2007-04-10
> **taurus said:**
> And you said you have Edgy on your machine.  Is that the old Celeron PC?

This is a different machine with ubuntu-feisty and it'a Celeron (TM) the other one you are mentioning is a Celereon Coppermine. the media players worked yesterday morning with no problem.  did you check through the out put I posted from terminal?

---

### Post by taurus on 2007-04-10
Perhaps you should look in the Feisty area to see if somebody who has the same problem as yours.  Otherwise, file a bug report since it is technically still a beta version.

---

### Post by DougieFresh4U on 2007-04-10
thanks for your help taurus. Between system freezes and no clue to why media players freeze up as well  I am currently reinstalling on that machine, why not I like reinstalling, NOT!!:mad: :mad:

---

