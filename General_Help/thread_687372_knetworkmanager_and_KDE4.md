---
title: "knetworkmanager and KDE4"
date: 2008-02-04
forum: General Help
---

### Post by .nedberg on 2008-02-04
I have a laptop with Hardy and KDE4.

With KDE3 knetworkmanager automaticly starts and connects to my wireless network. Under KDE4 it does not start and I have to start it manually.

I have tried ~/.kde4/Autostart and ~/.kde4/share/Autostart, but noen af them work.

How do I get KDE4 to automaticly connect to my wireless network?

---

### Post by Ferret-Simpson on 2008-04-17
Under Hardy, I use a hybridised desktop system. I have Kicker as my menu bar (Without an actual menu bar in it) - So it has my pager, system tray, clock, window list menu, system menu and k menu in.

Plasma acts as my desktop and as kind of a Dock bar - many many application shortcuts, plus a handy widget or two.

To do this, I used the xsessions...

/usr/lib/kde4/share/xsessions
/usr/share/xsessions

I copied the k3 apps I wanted from the latter to the former.

:)

---

