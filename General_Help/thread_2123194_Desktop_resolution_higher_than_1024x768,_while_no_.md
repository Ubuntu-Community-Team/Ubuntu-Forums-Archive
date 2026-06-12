---
title: "Desktop resolution higher than 1024x768, while no monitor connected, how?"
date: 2013-03-07
forum: General Help
---

### Post by SaturnusDJ on 2013-03-07
It's been years since I got this issue. Now I want to fix it.

The VNC setup I run is from this site: [http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/](http://seb.so/vnc-from-boot-without-logging-in-ubuntu-lubuntu-xubuntu-and-mint-lmde/)

- All those tutorials saying to add a resolution using xrandr don't work, because there is no resolution to choose if there's no monitor connected.

- [http://skerit.com/en/computer/english-vnc-x11-session-on-ubuntu-12-04-server-without-monitor-or-graphics-card/](http://skerit.com/en/computer/english-vnc-x11-session-on-ubuntu-12-04-server-without-monitor-or-graphics-card/)
Not working. I get a grey screen with correct resolution, but no desktop, only a gnome terminal window.

- [http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/6201-running-ubuntu-without-a-monitor-attached-x-fails.html](http://www.bsntech.com/bsntech-blog-mainmenu-321/computers-mainmenu-281/6201-running-ubuntu-without-a-monitor-attached-x-fails.html)
Sounds more to the root of the problem, but no GUI appearing. Later I found out the new xorg.conf location (/usr/share/X11/xorg.conf.d/) so I moved the conf file there. Same as tutorial above: Grey screen + terminal, no desktop.


What important for me in this is: Everything must continue running when the VNC clients disconnects.

Who has an idea to fix this?

---

### Post by SaturnusDJ on 2013-03-19
Kick!

---

### Post by SaturnusDJ on 2013-03-28
Kick again.

---

### Post by SaturnusDJ on 2013-04-12
Still hoping to fix this!!

---

### Post by SaturnusDJ on 2013-05-03
Here the proof of struggle: [http://ubuntuforums.org/showthread.php?t=1492111](http://ubuntuforums.org/showthread.php?t=1492111). :P

---

