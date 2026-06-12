---
title: "kwin: cannot connect to X server"
date: 2007-04-24
forum: General Help
---

### Post by bluenova on 2007-04-24
Hello all,

I have a problem whereby, when I try to start a new session in Kubuntu i.e. I'm already logged in and my girlfriend comes along and does '>switch user>start new session' several things don't always manage to start, most annoyingly kwin. Some things are starting fine such as kdesktop and klipper. Which is a bit strange. Below is the out take from .xsession-errors, most important bits:

Xlib: connection to ":0.1" refused by server
kwin: cannot connect to X server :0.1
kopete: cannot connect to X server :0.0

Does any one have any ideas? There seems to be very little about this issue when searching in Google. I have had the same issue with both OpenSuse and Kubuntu, even after removing all system files from the home dirs.


```
Xsession: X session started for hannah at Tue Apr 24 20:23:38 CEST 2007
startkde: Starting up...
startkde: kpersonalizer not found! Please install to properly configure your user.
kbuildsycoca running...
Xlib: connection to ":0.1" refused by server
Xlib: No protocol specified

kwin: cannot connect to X server :0.1
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kwin: cannot connect to X server :0.0
*** attempt to put segment in horiz list twice
/usr/bin/xmodmap:  unable to open file '/home/hannah.Xmodmap' for reading
/usr/bin/xmodmap:  1 error encountered, aborting.
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libunixprintplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/firefox/plugins/libunixprintplugin.so: undefined symbol: NP_GetMIMEDescription
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kerry: cannot connect to X server :0
kerry: ERROR: KUniqueApplication: Registering failed!
kerry: ERROR: Communication problem with kerry, it probably crashed.
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin.so: undefined symbol: NP_GetMIMEDescription
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin_oji.so: undefined symbol: NP_GetValue
nspluginscan: WARNING: Plugin doesn't implement NP_GetValue
kdecore (KLibLoader): WARNING: KLibrary: /usr/lib/mozilla/plugins/libjavaplugin_oji.so: undefined symbol: NP_GetMIMEDescription
kbuildsycoca running...
Reusing existing ksycoca
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kopete: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-7790' to 'kopete'
kopete: ERROR: Communication problem with kopete, it probably crashed.
kdecore (KProcess): WARNING: _attachPty() 12
Can't register passkey agent
Passkey agent already exists
kio (KSycoca): ERROR: No database available!
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813af18 ): KAccel object already contains an action name "file_quit"
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x813af18 ): KAccel object already contains an action name "file_quit"
QFile::open: No file name specified
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x0
No battery found.
This is not a laptop, quitting ... 
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x0
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x120
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  6
  Minor opcode:  0
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  6
  Minor opcode:  0
  Resource id:  0x0
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  6
  Minor opcode:  0
  Resource id:  0x0
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1a00fcd
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x1a00fcd
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1a0104a
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x1a0104a
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1a0104b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x1a0104b
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x120
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1a01065
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/hannah/.DCOPserver_desktop1__1
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x120
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x1a010eb
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/hannah/.DCOPserver_desktop1__1
and start dcopserver again.
---------------------------------

KDE Daemon (kded) already running.
kbuildsycoca running...
Reusing existing ksycoca
kio (KSycoca): ERROR: No database available!
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x120
kio (KIOConnection): ERROR: Could not write data
```

When I log out and log in again it all loads fine.

---

### Post by bluenova on 2007-04-25
Bump ^

---

### Post by bluenova on 2007-04-25
Bump ^

---

### Post by bluenova on 2007-05-01
Bump ^

---

