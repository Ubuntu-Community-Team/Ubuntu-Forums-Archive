---
title: "How to dynamically change configuration of a running Xserver?"
date: 2013-10-21
forum: General Help
---

### Post by ipejic on 2013-10-21
I'm running Ubuntu 12.04.3 on Intel's HD4000 GPU.

While Xserver is running, I would like to:


[LIST]
[*]add a new dummy screen to a running xserver (existing session, no DM involved)
[*]set resolution of a display inside newly created screen
[*]set the position of that screen to be right-of existing screen
[/LIST]

Bash or Python is preferred, however at this moment anything will help. 

(Intended use: As one or more of RaspberryPIs becomes available on my LAN (avahi or similar will help with this part) I would like to create new dummy screen on the central computer and expose it via x11vnc to be displayed on the PI. I don't need mouse, keyboard or any other input devices.)

---

