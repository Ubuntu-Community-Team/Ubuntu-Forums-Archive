---
title: "VNC at boot"
date: 2005-06-12
forum: General Help
---

### Post by tigerstripedcat on 2005-06-12
Anyone get VNC working at boot.  Like the other threads I found, I can get VNC working fine after kde starts (but not at the logon screen).  

I have installed:
tightvncserver
vncserver

and followed the instructions on this page:

[http://wiki.colinux.org/cgi-bin/VNC-On-Bootup](http://wiki.colinux.org/cgi-bin/VNC-On-Bootup) 

But I still can't access VNC until after kde starts.  Anyone have any HOWTO/Instructions they'd like to share?

---

### Post by intangible on 2005-06-17
Very simple, I've been using this for months, these are the instructions for gdm, but it should be almost identical for kdm:

Five Easy Steps:
[list=1]
[*] **System->Administration->Login Screen Setup**
Tab **XDMCP->Enable XDMCP** You can disable "Honor Indirect Requests"
For kdm or even xdm, just look through the settings and find XDMCP, make sure it's enabled.
[*] **sudo apt-get install vnc4server** (comes from universe)
[*] Put the following line at the end of **/etc/inetd.conf**:
```
5900    stream  tcp     nowait  nobody  /usr/bin/Xvnc Xvnc -inetd -desktop=LV-Tux -query localhost -IdleTimeout 7200 -depth 16 -once securitytypes=none
```
Replace "LV-Tux" with something you want the window title to be, usually the server name.
[*] **sudo /etc/init.d/inetd restart**
[*] Log out of your desktop (to restart gdm, xdm, or kdm)
[/list] 

That's it!  Try connecting from another machine and see how it goes.

---

