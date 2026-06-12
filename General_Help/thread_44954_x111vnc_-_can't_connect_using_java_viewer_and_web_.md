---
title: "x111vnc - can't connect using java viewer and web browser"
date: 2005-06-28
forum: General Help
---

### Post by Teo on 2005-06-28
Hi,
can't find a solution for my problem :/

I'm using Ubuntu Hoary 5.04, all packages (every single one in my system) are from Ubuntu repos.

I'm starting x11vnc with this a command:
```
x11vnc -httpdir /usr/share/tightvnc-java -httpport 5800
```
This is a result of command:
```
28/06/2005 13:43:30 Using X display with 32bpp depth=24 true color
28/06/2005 13:43:30 Autoprobing TCP port
28/06/2005 13:43:30 Autoprobing selected port 5900
28/06/2005 13:43:30 Listening for HTTP connections on TCP port 5800
28/06/2005 13:43:30   URL http://teo:5800
28/06/2005 13:43:30 screen setup finished.
28/06/2005 13:43:30 The VNC desktop is teo:0
PORT=5900

```
So everything should be OK. I can connect with my Ubuntu using vncviewer but I can't connect with my web browser (java-viewer) :/

Each time I'm tryin to connect from my web browser I got this message in terminal:
```
28/06/2005 13:43:38 httpCheckFds: fcntl: Invalid argument
```
What's this? Why this msg appears? On other machine with Mandiva everything is OK (I can connect using both: vncviewer and web browser).

Please don't reccomend me:
- Remote Desktop Sharing aka Vino
- FreeNX
- Xvnc (vncserver)
- xrfb0server
They just don't match my needs.

---

### Post by chusome on 2005-11-12
This config works for me in breezy...

---

### Post by Teo on 2005-11-12
[QUOTE=chusome]This config works for me in breezy...[/QUOTE]
It does not work in Hoary - x11vnc bin in repos is buggy.

---

