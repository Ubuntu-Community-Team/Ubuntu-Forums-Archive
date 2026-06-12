---
title: "headphones don't work with a external monitor"
date: 2021-04-19
forum: General Help
---

### Post by lucasokada on 2021-04-19
I'm with a problem. When I plug a external monitor,  ubuntu utilizes only this monitor to sound, even when I select the headphones on configuration. 
The problem isn't my hardware. When I do the same thing in the windows, it works and my ubuntu is already up to date.

---

### Post by TheFu on 2021-04-20
PulseAudio wants the last connected audio device to be used.  Try unplugging the headphones, AFTER the monitor is connected, then reconnect them.

Also, use pavucontrol to disable the monitor speakers (far right tab) and enable the headphones.   An of course, check that they aren't muted and that the sound level is at the recommended level (at least to start).

---

