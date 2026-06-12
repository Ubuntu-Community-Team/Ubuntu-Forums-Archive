---
title: "System instability, not quite a lockup"
date: 2007-10-29
forum: General Help
---

### Post by jimmy the saint on 2007-10-29
I will attempt to describe what is happening in as much detail as possible, because I really don't know how to troubleshoot it.

After using my gutsy system for a while, I notice that I no longer have internet access.  When I attempt to reconnect via the nm-applet on the gnome panel, it opens, responds, but seems to be stuck in a loop.  If I kill the process then restart it via the terminal, it closes itself shortly afterwords.
The entire system becomes unusable.  I can open most apps, but I cannot do anything with them.  For example, I can open the gnome "Add to panel" function, but if I attempt to add an app to the panel, the window freezes.  Other apps exhibit similar behaviors.

After a few minutes of this, the menus stop working.  If I hit ctr-alt-backspace, gnome reloads and I get to the logon screen.  When I attempt to log in all i get is an orange screen so I have to do a hard restart.  

This has happened consistently for the last few days on a relatively fresh gutsy installation.  I am at my wits end.  Any ideas on how to troubleshoot this?  I would hate to have to do another fresh install.

---

### Post by jimmy the saint on 2007-10-29
Please help me out here!!  I'm fairly new to Linux and I have no idea where to look for this!

---

### Post by dayvy on 2007-10-29
I have had mixed results with gnome network manager. I have seen it lock-up systems. My suggestion is to uninstall it. It's not needed. It's a convenience when you want to connect to a variety of networks. If you want an alternative then try wicd.

d.

---

### Post by jimmy the saint on 2007-10-29
So it could be the network manager causing the problem?  I will attempt to get rid of it and see what happens.  Thank you!  Like I said, I am coming from windows and my troubleshooting instincts are not serving me very well here.  I though the little applet was merely reporting what was going on under the hood, not actually doing anything itself.  Is the nm-applet the Gnome Network Manager?

---

