---
title: "Problem with NX (nomachine.com) on Windows 7 with Cygwin installed"
date: 2013-02-01
forum: General Help
---

### Post by oregonbob on 2013-02-01
I have used nomachine.com's NX to connect to gnome desktops on Ubuntu boxes for a long time. It usually works better/faster than any other remote desktop app such as VNC. I have recently encountered a problem connecting to a 12.04 even when using the custom "gnome-session --session=ubuntu-2d" settings in NX.

The problem appears to be a conflict with installed Cygwin and NX. When I attempt to start a gnome session with NX, Cygwin opens numerous "Cygwin/XFree X rl" processes and freaks out the screen, eventually preventing NX from making a successful session.

I can still run NX using a XFCE session just fine. But it freaks out if I try to use the preferred gnome-session.

---

