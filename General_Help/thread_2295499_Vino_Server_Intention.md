---
title: "Vino Server Intention"
date: 2015-09-19
forum: General Help
---

### Post by Jason_Hunter on 2015-09-19
I don't understand why vino-server is not system-wide remote access service, or is it?

It seems to be like it is intended to share desktop once you're logged in?

What if you're not logged in? 

I've seen many hacks to make it start on system bootup, but it doesn't seem like it's its intention?

Are we supposed to run a different service for system-wide remote access?

---

### Post by steeldriver on 2015-09-19
Not sure I understand what you mean by "system-wide" in this context - remember that desktop sessions belong to individual users, and *nix is inherently a multi-user system

There are basically two different kinds of VNC server: those intended for sharing the "real" desktop of a system (vino-server, x11vnc), and those intended to run completely independent (potentially multi-user) virtual desktop sessions on a remote server (vnc4server, tightvncserver)

If you want to be able to run a remote session without already being logged in locally to the target machine, then you really have two choices AFAIK:

[LIST=1]
[*]run a "desktop sharing" type of VNC server *under the display manager - *I've done this with x11vnc, but not tried with vino 
[*]log in non-graphically i.e. via SSH, and then start an "independent session" type VNC server 
[/LIST]

As a variant on (2) you could start an independent VNC session for each user at boot time, to save the step of having to log in via CLI first

Whichever approach you take, you should remember that VNC is not a secure protocol and you should take steps to secure the connection e.g. by tunelling it over VNC. There are 3rd party products such as x2go that IIRC implement SSH tunnelling under the hood.

---

### Post by Jason_Hunter on 2015-09-19
I just don't understand why vino server, which is a desktop sharing type of vnc server is somehow the default for Ubuntu. 

It's like we're stuck in '99. 

GNU/Linux is a multi-user operating system and yet, they default to something which you have to be logged in, to use. It just seems like utter stupidity to me.

---

### Post by cmcanulty on 2015-09-19
try x11rdp or xrdp see this link as the repos version has some issues. I agree this really needs work especially as vino requires you to turn off encryption or it doesn't work.
[http://scarygliders.net/x11rdp-o-matic-information/]("http://scarygliders.net/x11rdp-o-matic-information/")

---

