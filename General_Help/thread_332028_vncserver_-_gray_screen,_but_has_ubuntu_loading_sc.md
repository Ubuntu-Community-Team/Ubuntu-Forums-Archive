---
title: "vncserver - gray screen, but has ubuntu loading screen"
date: 2007-01-05
forum: General Help
---

### Post by talz13 on 2007-01-05
So on my fresh install of edgy, I thought I'd try getting VNC setup again.  All was going smoothly (after I got the sshd sorted out), installed vncserver from synaptic, and went to start it up.

When I ran vncserver :1, it looked like it was going fine:
```
jeff@server:~$ vncserver :1

New 'X' desktop is server:1

Starting applications specified in /etc/X11/Xsession
Log file is /home/jeff/.vnc/server:1.log

jeff@server:~$ 


```

And there wasn't anything that I found suspicious in the vnc log:
```

05/01/07 12:40:19 Xvnc version 3.3.7 - built Jul  4 2006 10:06:30
05/01/07 12:40:19 Copyright (C) 2002-2003 RealVNC Ltd.
05/01/07 12:40:19 Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
05/01/07 12:40:19 All Rights Reserved.
05/01/07 12:40:19 See http://www.realvnc.com for information on VNC
05/01/07 12:40:19 Desktop name 'X' (server:1)
05/01/07 12:40:19 Protocol version supported 3.3
05/01/07 12:40:19 Listening for VNC connections on TCP port 5901

05/01/07 12:44:22 Got connection from client 0.0.0.0
05/01/07 12:44:22 Protocol version 3.3
05/01/07 12:44:22 Pixel format for client 0.0.0.0:
05/01/07 12:44:22   16 bpp, depth 16, big endian
05/01/07 12:44:22   true colour: max r 15 g 15 b 15, shift r 12 g 8 b 4
05/01/07 12:44:22 Using ZRLE encoding for client 0.0.0.0
05/01/07 12:44:22 rfbProcessClientNormalMessage: ignoring unknown encoding type 7
05/01/07 12:44:22 rfbProcessClientNormalMessage: ignoring unknown encoding type 6
05/01/07 12:44:22 rfbProcessClientNormalMessage: ignoring unknown encoding type 8

```

But when I went to connect to the vnc server from another machine, all that happened was this:

[img]http://www.talz13.com/downloads/images/vncserverStalls.jpg[/img]

It displays the gray background and X cursor like I used to get, but now it also shows the ubuntu loading screen on there as well!  I've never seen it do that when it still fails to get to a workable desktop.  I've given it about 10 minutes now, and it's not going anywhere, so I'm pretty sure it's not just taking a long time to load.

---

### Post by kdnewton on 2007-01-12
I'd posted the same thing this afternoon in another section of these forums. When I came back to the session 7 hours later the Ubuntu load screen was still there. tightvncserver hasn't fixed the problem, in fact it doesn't even start the load screen. And I haven't had any luck with vnc4server. I'm looking forward to a solution.

---

### Post by lofftjm on 2007-01-22
I have the same issue...

---

### Post by Ixzat on 2007-02-07
Me too, just started digging through it though...

---

### Post by lavasurfer on 2007-02-16
Here is what I did to solve this
First I loaded xterm in the xstartup file and in the xterm typed
gnome-session
this reported an error that the depth of 32 I had set in my vnc.conf file was not supported
so in the /etc/vnc.conf file make sure you have it set to 16 and you should load fine

sudo gedit /etc/vnc.conf
find the $depth line
set it as so:
$depth = "16";

Scooter

---

