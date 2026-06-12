---
title: "VNC Help.........."
date: 2008-06-25
forum: General Help
---

### Post by childsce on 2008-06-25
I'm getting the following error in the log file and I'm unable to connect.

> vnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Wed Jun 25 11:02:25 2008
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
/root/.vnc/xstartup: 12: twm: not found
FreeFontPath: FPE "/usr/share/fonts/X11/misc/" refcount is 2, should be 1; fixing.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":1.0"
      after 173 requests (172 known processed) with 0 events remaining.
xterm:  fatal IO error 11 (Resource temporarily unavailable) or KillClient on X server ":1.0"

I followed the instructions exactly from this thread
[http://ubuntuforums.org/showthread.php?t=197964](http://ubuntuforums.org/showthread.php?t=197964)


I'm running Ubuntu 8.04

thanks for the help

---

### Post by ryanhaigh on 2008-06-26
Perhaps you would be better served asking for help in the thread you referenced. It seems like twm is missing you can probably install it using ```
sudo apt-get install twm
```. That said I am quite sure that twm is not what you want to be using as your window manager. Is there any particular reason you can't use the built in vpn server.

In any case this documentation may be useful to you: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

