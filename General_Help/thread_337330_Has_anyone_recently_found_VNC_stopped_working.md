---
title: "Has anyone recently found VNC stopped working"
date: 2007-01-12
forum: General Help
---

### Post by grahams on 2007-01-12
I have 2 systems running edgy VNC stopped working on both with the same symptoms "ReadFromRFBServer: rdr::EndOfStream". 

I haven't made changes to either system apart from periodic software updates "apt-get update" "apt-get upgrade"

Is anyone else running into the same issue?

---

### Post by Atomic Dog on 2007-01-12
Are you talking about the client?  So far it has been fine.  I use it all the time.

---

### Post by foxmulder881 on 2007-01-12
What's VNC used for? I've seen it there many times but don't even know what it's for.

---

### Post by grahams on 2007-01-12
This is the output I get from vncviewer, which has been working for months and now stopped on 2 systems and I can't think of any common thread. I think the error is coming from vncserver. 

$ vncviewer :1
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.8 (viewer 3.3)
Password: 
ReadFromRFBServer: rdr::EndOfStream

---

### Post by PilotJLR on 2007-01-12
> **foxmulder881 said:**
> What's VNC used for? I've seen it there many times but don't even know what it's for.

remote desktop, aka terminal services

---

### Post by grahams on 2007-01-16
Looks like Xvnc stopped running. 
 
ps -ef |grep vnc
grahams1  7400  5040  0 09:18 pts/0    00:00:00 grep vnc

If I start it manually I get "error opening security policy file /etc/X11/xserver/SecurityPolicy"
This file doesn't appear to exist. Any clues anyone?

 sudo Xvnc :2 -query localhost -geometry 1280x1024 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Tue Jan 16 09:09:42 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5902
 vncext:      created VNC server for screen 0
error opening security policy file /etc/X11/xserver/SecurityPolicy
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing

---

### Post by grahams on 2007-01-17
Fixed :D 

There is an issue with the latest vnc4server see bug [https://bugs.launchpad.net/ubuntu/+s...nc4/+bug/78282](https://bugs.launchpad.net/ubuntu/+s...nc4/+bug/78282)

Downgrading vnc4server cures the issue until the bug is fixed.

---

