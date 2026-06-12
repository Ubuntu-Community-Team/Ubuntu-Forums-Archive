---
title: "Some keys not working on USB keyboard"
date: 2013-09-20
forum: General Help
---

### Post by Anaxagore on 2013-09-20
Hi,

I have had a strange experience with my keyboard. I use my laptop on its docking station with an external USB keyboard (Logitech illuminated keyboard). Somehow overnight some keys began not to work anymore on this keyboard (all keys still work fine on my laptop, but the position of the laptop's keyboard is far from being ergonomic...

Keys that do not work anymore: 1, 6 (on the number bar, not on the numeric keypad where everthing seems to work), y, g, the left Alt key (the right one similar to AltGr in US Alternative International configuration, still works).


Does anyone have an idea of what may be causing this issue? I'd like to discard any software-related issue before purchasing a new keyboard. I went through the forums here but mostly found notes with the reversed issue (seemingly dead keays on laptop keyboard but external one working fine) and none could help..

Thanks in advance for your answers!

Configuration:
Ubuntu 12.10 x64
Dell Precision M6600
Logitech Illuminated Keyboard
(Unity deactivated to reverse to an Ubuntu 10.x looking desktop)

---

### Post by tgalati4 on 2013-09-20
Open a terminal:

```
xev
```

Put the mouse in the xev window then start typing one key at a time.  Note the keycode for each key.  You will get a keycode for pressing and another for releasing each key.

Because the keyboard is connected to a dock, it's possible that static electricity has zapped it.  Do you get a shock sometimes when connecting the laptop to the dock?

---

### Post by CatKiller on 2013-09-20
It might just be dirt.

---

### Post by Anaxagore on 2013-09-22
Indeed my keyboard is dead.. xev did not react at all when pressing those keys, and using the keyboard with a Windows machine also produced the same problems. A dust blower did not fix the problem.RIP Logitech Illuminated keyboard.. Thanks for all your suggestions!

---

