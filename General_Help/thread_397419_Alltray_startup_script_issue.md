---
title: "Alltray startup script issue"
date: 2007-03-30
forum: General Help
---

### Post by Cornbreadly on 2007-03-30
The issue is that it doesnt work

I think I have it set up correctly here...

```

#!/bin/sh

#katapult
alltray katapult &

#swiftfox
alltray /opt/swiftfox/swiftfox &

#amarok
alltray amarokapp &

#ktorrent
alltray ktorrent &

#beagle
alltray beagled &

#nautlis
alltray nautilus &

```

I have it saved as .startme and in session manager I have 


chmod +x /home/eric/.startme


Where did I mess up?

---

### Post by spin2cool on 2007-03-30
The chmod command just changes a file's permissions so that it can be executed.  It does not actually execute the code.  The startup command would just be "/home/eric/.startme".  Or "sh /home/eric/.startme"

---

### Post by Cornbreadly on 2007-03-30
I did what you advised and I think we are closer because when I type sh .startme into the terminal, it works. 

But it doesnt seem to work when I boot up, and I have "sh .startme" as an entry in the start up tab of the session manager.

---

### Post by spin2cool on 2007-03-30
You need to provide the full path to the .startme script in session manager, since your home directory isn't in your PATH, like /usr/bin is.  

instead use "sh /home/eric/.startme", as I specified before.

---

### Post by Cornbreadly on 2007-03-31
I did as you said and It did not work.

I am getting alot of info when I run it in the terminal.  Could it have something to do with it?

```

eric@eric-desktop:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-eric"
Link points to "/tmp/ksocket-eric"
kdeinit: Shutting down running client.
---------------------------------
It looks like dcopserver is already running. If you are sure
that it is not already running, remove /home/eric/.DCOPserver_eric-desktop__0
and start dcopserver again.
---------------------------------

Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  147
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
WARNING: Waiting for already running klauncher to exit.
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
Link points to "/tmp/kde-eric"
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
kbuildsycoca running...
Ignored duplicate item: NmapFE
Ignored duplicate item: MGM System Monitor
Ignored duplicate item: Dictionary
Ignored duplicate item: Amaya 9.53
Ignored duplicate item: QCaD
Ignored duplicate item: kFlickr
Ignored duplicate item: CD/DVD Writer GnomeBaker
Ignored duplicate item: Gnumeric Spreadsheet
Ignored duplicate item: Remove orphaned packages
Ignored duplicate item: Simple Backup Restore
Ignored duplicate item: Firestarter
Ignored duplicate item: Simple Backup Config
Ignored duplicate item: Software Sources
Ignored duplicate item: System Log
Ignored duplicate item: Windows Wireless Drivers
Ignored duplicate item: GNOME Partition Editor
Ignored duplicate item: Shared Folders
Ignored duplicate item: Update Manager
Ignored duplicate item: Networking
Ignored duplicate item: Time and Date
Ignored duplicate item: Keyring Manager
Ignored duplicate item: System Monitor
Ignored duplicate item: Login Window
Ignored duplicate item: BootUp-Manager
Ignored duplicate item: Services
Ignored duplicate item: Users and Groups
Ignored duplicate item: Network Tools
Ignored duplicate item: The Mozilla Organization
Ignored duplicate item: Documentation
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80966f0 ): KAccel object already contains an action name "play_pause"
QLayout "unnamed" added to QVBox "unnamed", which already has a layout
kdecore (KAction): WARNING: KAction::insertKAccel( kaccel = 0x80966f0 ): KAccel object already contains an action name "play_pause"
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
STARTUP
QObject::disconnect: Unexpected null parameter
QObject::connect: Cannot connect (null)::activePartChanged( KParts::Part * ) to KHTMLPart::slotActiveFrameChanged( KParts::Part * )
eric@eric-desktop:~$ 
eric@eric-desktop:~$ 

```

---

