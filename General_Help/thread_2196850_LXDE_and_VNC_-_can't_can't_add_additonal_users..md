---
title: "LXDE and VNC - can't can't add additonal users."
date: 2013-12-31
forum: General Help
---

### Post by prayner.basil on 2013-12-31
Hi
with help from this forum, I got VNC working for root. to allow access the an Ubuntu server sitting atop XenServer.

I want to add users to VNC to allow others access from outside my network. (I've implemented tunnelling via SSH- which works for root).

So far, I've:
[LIST]
[*]created a user in Ubuntu (fsmith), and logged into Ubuntu via Putty from my Windows box.
[*]tried to connect using TightVNC client - with error "Couldn't connect to localhost:5902. Connection refused:connect"
[*]In /etc/vncserver/vncservers.conf, I created additional entries -
[LIST]
[*]VNCSERVERS="1:vncuser 2:fsmith"
[/LIST]
[/LIST]
[INDENT=2]VNCSERVERARGS[1]="-geometry 1024x768 -localhost"[/INDENT]
[INDENT=2]VNCSERVERARGS[2]="-geometry 1024x768 -localhost"
[/INDENT]

[LIST]
[*]When I use VNC - I used localhost:5902 (after logging in via Putty)
[/LIST]

I obviously missed something when I read through the tutorials - but I currently can't find it. Any advice welcome!

---

### Post by steeldriver on 2013-12-31
Are you adding the additional tunnel (i.e. L5902:localhost:5902) to your putty session?

Did both vnc servers start successfully on the server? (check with ps) 

Did you run vncpasswd to set up initial VNC credentials for the fsmith account?

---

### Post by prayner.basil on 2014-01-01
I think the answer appears to be yes for all questions. 
fsmith has a .vnc folder in his home directory.
To remove vnc accounts, do I simply remove the .vnc directory from their home directories?
Checked Putty and it's OK.
Tried to trawl through Google searches to find more info without luck.

---

