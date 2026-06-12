---
title: "remote desktop (vnc, xdmcp)"
date: 2007-04-06
forum: General Help
---

### Post by loveshocked on 2007-04-06
Hi all, 

i am a new ubuntu user.
 I am still trying to figure out about the remote desktop. I was wondering whether there is a remote desktop based installation than allow a lot of user to login in a same time (sort of like windows server, where there are USERS, that can login in a same time)
hopefully, this software is capable of doing a remote desktop from windows as the clients.

I tried vnc once, but it is just for one user at the same time, and xdmcp, which is not ready to be remoted from windows. I am using ubuntu edgy.



Thanx for the infos :-D

---

### Post by solar george on 2007-04-06
You can use xdmcp,

Install cygwin/X [http://x.cygwin.com/]("http://x.cygwin.com/")

and follow [these instructions]("http://x.cygwin.com/docs/ug/using-remote-session.html")

---

### Post by Punker on 2007-04-06
I suggest you install a firewall or do a iptables script their is lots of info around this forum

---

### Post by loveshocked on 2007-04-06
What I read in the guides, 'Click Options at the lower left corner of the login screen
Select "Remote Login via XDMCP" ' 
so I assume, the Clients are also using ubuntu.
What if the clients are using windows, can they also use XDMCP client?


Thanx again

---

### Post by srhlefty on 2007-04-06
solar george has it right, that is what works for windows--install cygwin/X, then you just do something like

XWin.exe -query 192.168.1.1

replacing 192.168.1.1 with your ip of course :)

---

### Post by loveshocked on 2007-04-06
I tried to install VNC, following 

but what i get when I type[COLOR="Lime"] vncviewer localhost:1[/COLOR]

VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.

(stop right there,didn't happen anything)

n if i type [COLOR="Lime"]vncviewer localhost:0[/COLOR]

 vncviewer localhost:0
VNC viewer version 3.3.7 - built Jul  4 2006 10:04:48
Copyright (C) 2002-2003 RealVNC Ltd.
Copyright (C) 1994-2000 AT&T Laboratories Cambridge.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
VNC server supports protocol version 3.7 (viewer 3.3)
Password: 
VNC authentication failed

(the manual in [this]("http://ubuntuforums.org/showthread.php?t=122402") thread said that it should be localhost:1)

n what I get when I typed [COLOR="Lime"]grep xinetd /var/log/syslog[/COLOR]

Apr  7 00:48:05 loveshocked-ubuntu xinetd[22646]: warning: can't get client address: Transport endpoint is not connected

[COLOR="Black"]I am getting confused about this.. Thanx 4 the answer[/COLOR]

---

### Post by firefoxman on 2007-04-08
Try this: [http://freedesktop.org/wiki/Xming](http://freedesktop.org/wiki/Xming)

It works for me.

---

### Post by UncleB on 2007-04-10
I used [Cirrocco's method from this thread.]("http://ubuntuforums.org/showthread.php?t=197964&highlight=vnc4server")

I use it to connect from Windows VNC and from Linux and OSX viewers.

There were a couple of issues for me with it: chiefly the path to the fonts folder and the version of vnc4server used. On page 2 are the fixes I used to get it working.

You shouldn't need Cygwin to VNC in.

Good luck!

---

