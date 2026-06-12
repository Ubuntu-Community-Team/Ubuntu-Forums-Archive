---
title: "Disabled touchpad"
date: 2015-04-24
forum: General Help
---

### Post by jfanghanel on 2015-04-24
i accidentally disabled my touchpad. how can i re-eneble it via command mode?

---

### Post by slickymaster on 2015-04-24
Hi jfanghanel, welcome to the forums.

I moved your post to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by mc4man on 2015-04-24
typically - 
```
gsettings set org.gnome.settings-daemon.peripherals.touchpad touchpad-enabled true
```
(- side note of little value -  On unity (14.04 ) a log out/in or suspend/awake usually re-enables it (a bug never fixed in 14.04

---

