---
title: "Which edition for Samba?"
date: 2008-04-28
forum: General Help
---

### Post by markjlewis on 2008-04-28
I want to build a simple file server to use with a small home network of windows PCs (XP & Vista). Which edition (desktop or server) would be best to use to install Samba on to do this? I'm a Ubuntu novice but have had a several years of experience of Sun Solaris (but this was a few years ago so am a bit rusty :) )

Cheers

Mark

---

### Post by rturner on 2008-04-28
If it's strictly a file server, from a resources standpoint, the server version would be best.  If you've got a fast machine, then you could put the desktop version on it. I'm using my desktop version for a testing lamp server and it works fine and fast from my other machines.  But it's getting very limited use as a lamp server. If you're really rusty, it might be slightly more advantageous to use the desktop, but to tweak samba the way you want it, I find it easier to use the command line.  I know the server version lets you add the lamp server from the intall gui;  I don't remember if you can add samba from that as well, but it's trivial to set up, either way.  Lots of how-tos here.

---

### Post by ryanhaigh on 2008-04-28
I would just go with the desktop edition, there is no real advantage for using the server edition in this situation unless you expect really heavy loads or are overly worried about security.

---

