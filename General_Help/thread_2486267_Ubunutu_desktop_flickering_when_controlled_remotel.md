---
title: "Ubunutu desktop flickering when controlled remotely"
date: 2023-04-25
forum: General Help
---

### Post by lopilop on 2023-04-25
Hi

I just installed Ubuntu 22.04 on an old Intel Mac Mini.
I works well, but I have an issue with remote access.
Whether I'm using Teamviewer or VNC, when accessing Ubuntu from my windows pc the desktop flickers on and off and the control of the desktop is extremely slow.

Any Ideas what to look for?

---

### Post by TheFu on 2023-04-25
Don't use VNC.  Use x2go instead.  [https://wiki.x2go.org/doku.php](https://wiki.x2go.org/doku.php)  Then you can set the connection settings to meet your hardware, network, and other needs.

BTW, no remote desktop tools work well with desktop environments that want direct access to a GPU, so don't bother with Gnome or KDE.  The result is poor or won't work.  Use XFCE, LXQt, Mate or some other light DE instead.  This is probably the main reason for your issue, but x2go is 2-3x faster than VNC or RDP.

---

