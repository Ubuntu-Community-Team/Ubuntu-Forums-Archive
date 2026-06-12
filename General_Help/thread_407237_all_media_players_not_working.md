---
title: "all media players not working"
date: 2007-04-11
forum: General Help
---

### Post by DougieFresh4U on 2007-04-11
This happened a couple of days ago where I open media player, select song and player frezes up. ALL PLAYERS, amarok, beep, Listen, Exaile. I  reinstalled Ubuntu and loaded a couple of songs yesterday and ALL PLAYERS worked. Today, ALL PLAYERS do not work. Here is output from terminal when trying to start players from terminal. Can some one please look over and see if some thing is missing or "broke". Thank you very much::dougie@DougiesToyBox:~$ exaile
/usr/share/exaile/xl/xlmisc.py:42: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon
/usr/lib/python2.5/site-packages/mutagen/m4a.py:41: DeprecationWarning: mutagen.m4a is deprecated; use mutagen.mp4 instead.
  "mutagen.m4a is deprecated; use mutagen.mp4 instead.", DeprecationWarning)
Error grabbing key 162, 0x855b018
Plugins 'Alarm Clock' version '0.1' loaded successfully
Plugins 'Desktop Cover' version '0.1' loaded successfully
Plugins 'LibNotify Plugin' version '0.1' loaded successfully
Plugins 'Mini Mode' version '0.1' loaded successfully
Plugins 'Serpentine Plugin' version '0.1' loaded successfully
Plugins 'Streamripper!' version '0.1' loaded successfully
Created db for thread Thread-1
{'Thread-1': <sqlite3.Connection object at 0x877df20>}
mmkeys are available.
loading tracks...
Closed db for thread Thread-1
done loading tracks...
loading songs
Clearing tracks cache
dougie@DougiesToyBox:~$ amarok
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
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8140058 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x8140058 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
Amarok: [Loader] Amarok is taking a long time to load! Perhaps something has gone wrong?
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2c0003e
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
kio (KIOConnection): ERROR: Header read failed, errno=104
kio (KIOConnection): ERROR: Header has invalid size (-1)
Amarok: [Loader] amarokapp probably crashed!
dougie@DougiesToyBox:~$ listen
No musicbrainz support (musicbrainz2 missing)
No iPod support
No Audio cd support (musicbrainz2 missing)
Error grabbing key 162, 0x8535c18
/usr/lib/listen/widget/tray.py:45: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  try: import egg.trayicon
0 songs and 3 playlists saved
Exit successful

---

### Post by DougieFresh4U on 2007-04-12
Any body please care to take a guess?

---

### Post by SkiesOfAzel on 2007-05-06
Did you update after reinstalling? Maybe an updated package is broken.

---

### Post by mtschaef on 2007-07-13
I'm having the same problem as you are with this!  I think that happened as I had Amarok playing some music and I was trying to save a file when I heard a command prompt beep (Screen Flash) and then all sounds stopped playing/working.  Including GAIM IM.
I have tried VLC as well and nothing will play... I have to do a Reboot and then it is all better!  I think I'm going to try to turn of my Command Beep to see if that fixes it.  
Please let me know if you find a fix as well!

IT WORKED!
System > Preferences > Sound
I set all of the 'Devices' to be ALSA instead of Autodetect
Then goto the 'System Beep' tab and unCheck the 'Enable system beep'
Then Close.

I DIDN'T even have to logout and back in!  That fixed it.
Hope it works for you if you run into the problem again!  And for anybody else!

---

