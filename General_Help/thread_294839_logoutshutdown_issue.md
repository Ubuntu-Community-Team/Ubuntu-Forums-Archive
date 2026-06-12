---
title: "logout/shutdown issue"
date: 2006-11-07
forum: General Help
---

### Post by ravenon on 2006-11-07
I have seen many posts out trouble in Edgy with the logout/shutdown buttons in the chooser. I am running 32 bit Edgy on a 64 bit Turion with X700 graphics using fglrx driver (a laptop). If I hit the chooser button in the upper right hand corner an choose logout or shutdown--screen goes white and only a power button push will shut the machine down.
My cure found by reading bug reports was to add
AlwaysRestartServer=true in /etc/gdm/gdm.conf-custom in the [daemon] section.

After restarting, I have logout and in several times and all seems to work fine.

Curious point: this machine dual boots the 64 bit version where the problem has not manifested. I also have another desktop replacement type laptop with a Pentium IV Radeon 9700 graphics running with the fglrx driver and the problem never has manifested. From the various posts I have seen and the bug reports, the problem seems like a ghost--only appearing on some machines/hardware and only sometimes.

Addition: Fix one thing, break another; the laptop will now not suspend.

---

