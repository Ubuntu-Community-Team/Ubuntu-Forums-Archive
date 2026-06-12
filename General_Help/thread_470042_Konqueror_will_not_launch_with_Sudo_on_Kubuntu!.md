---
title: "Konqueror will not launch with Sudo on Kubuntu!"
date: 2007-06-10
forum: General Help
---

### Post by cookies on 2007-06-10
Okay, this isn't my error, but some one else who needs help

whenever they type in Konsole

sudo konqueror they get

X Error: BadDevice, invalid or uninitialized input device 168
Major opcode:  145
Minor opcode:  3
Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
Major opcode:  145
Minor opcode:  3
Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Link points to "/tmp/kde-root"
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
kded: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-20916' to 'kded'
kded: ERROR: Communication problem with kded, it probably crashed.
konqueror: WARNING: Can't open /root/.kde/share/apps/konqueror/bookmarks.xml
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified
knotify: cannot connect to X server :0.0
DCOP aborting call from 'anonymous-20920' to 'knotify'
ERROR: Communication problem with knotify, it probably crashed.

I also get the same-ish error when I try this on the Kubuntu LiveCD.

---

### Post by harty83 on 2007-06-10
Whenever I launched something graphical, I used try "kdesu" instead of "sudo." Give it a shot.  Not for sure if it will cure your problem.  

It's been a while since I've used KDE, but I remember having similar problems when trying to run a gui program as root.  It seems to me that I fixed that by logging into kdm once as root which has to be enabled. 

Like I said, its been a while since I've used KDE so I'm not saying they are for sure cures but give them a try anyway.

---

### Post by cookies on 2007-06-11
I'll try that, thanks.

---

