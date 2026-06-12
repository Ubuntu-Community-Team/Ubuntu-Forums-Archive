---
title: "My General Problems - First Post"
date: 2007-06-19
forum: General Help
---

### Post by seodavid on 2007-06-19
Firstly Hello to the Ubuntu community, and secondly I hope I have posted in the right place :roll:

I first installed Ubuntu Server Edition onto my Dell Poweredge 1900, without realising it was text only. And as im new to linux I removed that and put on Ubuntu Desktop Edition, for the GUI.

What im tring to end up with:
[LIST]
[*]Move my Teamspeak Server from a old windows XP home pc to Ubuntu
[*]Move Armagetron Advanced Server from the same box to Ubuntu
[*]Make a new webserver and move content from old box to Ubuntu
[*]Get MySQL running on it
[*]Install a VNC server, simular to Ultra VNC on the XP box.
[/LIST]

What I have managed to do so far:
[LIST]
[*]Move my Teamspeak Server from a old windows XP home pc to Ubuntu, but have this problem:
[img]http://xs216.xs.to/xs216/07252/teamspeak-problems.png[/img]
It works over the lan, but on externally, which it did on XP
[*]Make a new webserver and move content from old box to Ubuntu - Done
[*]Move Armagetron Advanced Server from the same box to Ubuntu, this I have managed.
[*]Install a VNC server, simular to Ultra VNC on the XP box. - Attempted to do, but failed
[*]Get MySQL Server running on it -  Again not started.
[/LIST]

Sorry that its quite a long post but its a post of *help this is were im hitting problems*

---

### Post by seodavid on 2007-06-20
Gave up on that tack, so formated, re-installed with the server.

Followed this guide:
[http://ubuntuforums.org/showthread.php?t=236834&highlight=set+up+teamspeak+server](http://ubuntuforums.org/showthread.php?t=236834&highlight=set+up+teamspeak+server)

But where it comes to editing the ini, I had problems, as it kept doing things i did not expect. (e.g. pressing 1 stuck in a load of "~")

So after a little forum looking i ran the command:
"sudo aptitude install ubuntu-desktop"

Teamspeak has finally gone in, but I had to use the following commands:
```
sudo iptables -A INPUT -p tcp --dport PORTNUMBER -j ACCEPT
```
```
sudo iptables -A INPUT -p udp --dport PORTNUMBER -j ACCEPT
```

To allow the ports.

---

