---
title: "Tightvnc problems in windows xp"
date: 2006-10-19
forum: General Help
---

### Post by eklypse on 2006-10-19
I am trying to get a remote desktop in Windows Xp pro.  I am using tightvnc.  When I run tightvncserver I get:

> couldn't start xtightvnc; trying default font path 
Please set correct fontPath in tightvncserver script.

Then when I connect VIA windows tightvnc program I can connect but only using the terminal and I want to access Gnome.  Also when I try to run xinit it gives me:

> X: warning; process set to priority -1 instead of requested priority 0
_XSERVTransSocketINETCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running


But I can open programs like xeyes and gedit fully.  Just cannot control the desktop.  What I want to do is remotely access my desktop in ubuntu from windows and I would like it to be a shared access so that I can control programs remotely on my ubuntu system in the Gnome desktop and then disconnect and what ever programs I started are still running on the ubuntu system.  :confused: :confused:

---

### Post by ATAQ on 2006-10-19
Maybe you could consider running a different VNC server in XP, like RealVNC or something, I dont know much about windows but I presume it may be an application fault. Also check that you have the ports open on the XP firewall, that is if you have one,
Hope this helps,
Regards,
Ant,
Eire

---

