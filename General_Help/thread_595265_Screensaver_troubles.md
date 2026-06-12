---
title: "Screensaver troubles"
date: 2007-10-28
forum: General Help
---

### Post by 67GTA on 2007-10-28
I have not been able to get any of the screensavers to activate since Gutsy beta 3. I tried the command line today, and got some xserver errors. I'm still trying to run this bug down. Without a screensaver, I have to shut my PC down constantly to protect my LCD screen. Anyone have any ideas?

root@fastback:/home/shawnr# '/usr/bin/X11/kpolygon.kss'
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kpolygon.kss: cannot connect to X server :0.0
root@fastback:/home/shawnr# /usr/bin/X11/kpolygon.kss
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kpolygon.kss: cannot connect to X server :0.0
root@fastback:/home/shawnr# '/usr/bin/X11/krotation.kss'
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

krotation.kss: cannot connect to X server :0.0
root@fastback:/home/shawnr# '/usr/bin/X11/ksolarwinds.kss'
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

ksolarwinds.kss: cannot connect to X server :0.0

---

### Post by kellemes on 2007-10-28
You seem to be running as root..
Does it run as a regular user?

---

### Post by 67GTA on 2007-10-28
I was running some other commands, when it hit me to try the screensaver commands. It is the same error with regular user. I was trying to find out where the bug had originated, and found this thread on the Debian forums: [http://forums.debian.net/viewtopic.php?t=13487&highlight=screensaver](http://forums.debian.net/viewtopic.php?t=13487&highlight=screensaver)

This fixed mine. It activates when it is supposed to.

---

