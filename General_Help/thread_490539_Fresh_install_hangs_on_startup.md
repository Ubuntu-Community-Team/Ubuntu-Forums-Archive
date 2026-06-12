---
title: "Fresh install hangs on startup"
date: 2007-07-02
forum: General Help
---

### Post by Diiba on 2007-07-02
Hi, just installed ubuntu after few months usage of Zenwalk, and I ran in to a problem, I can't get the system to start. Whenever I try to normally boot ubuntu, the startup just stops on the last section of load bar, I however can go in to the recovery mode, and from there hit startx command, and start using ubuntu normally. (I'm running on a Celeron 700mz/128mb ram system, and planning on changing to fluxbox soon as I get my system working).
Any help appreciated.

Edit// After some checking out I managed to get in to the normall bash shell, when I tried to log in from there I got this (   65.784000) BUG: soft lockup detected on CPU#0!
Edit2// Kinda fixed, only boots when wlan card (DWL-g630) is popped out.

---

### Post by RedSquirrel on 2007-07-03
Are you trying to run GNOME on those specs?

I would just do a barebones install with Fluxbox and build up from there:

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

---

