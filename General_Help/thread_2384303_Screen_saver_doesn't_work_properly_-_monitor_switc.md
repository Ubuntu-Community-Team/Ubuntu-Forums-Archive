---
title: "Screen saver doesn't work properly - monitor switches back on (16.04 arm64)"
date: 2018-02-05
forum: General Help
---

### Post by xrayed on 2018-02-05
Hi there,
I am using Ubuntu 16.04 on a Arm64 type of system (Nvidia Jetson).
Unfortunately I experience the following issue - after a period of inactivity the monitor goes off (as intended), but after roughly 10 seconds in turns on again, but completely blackened (sometimes with a mouse cursor visible).
I have experimented a lot so far:
- tried to disable gnome-screensaver (including chmod -x /usr/bin/gnome-screensaver)
- experimented with "xset dpms" settings and "xset s" settings 

Nothing helped. The monitor just turns back on. I read about "vbetool", but it's not available on Arm64.

Any ideas/hints what to try? As it seems the problem is somewhere in  X11, not in Gnome. As even "xset dpms force off" doesn't work properly. Especially weird - after "xset s noblank; xset dpms force off" the screen turns back on with a strange grey picture. After "xset s noexpose; xset dpms force off" the screen turns on again and showing the desktop, but after hitting a key it turns for 1-2 seconds off again and then on. "xset s off" doesn't help either.

I've also tried:
setterm -blank 5 -powersave powerdown -powerdown 5

setterm: terminal xterm-256color does not support --blank
setterm: cannot (un)set powersave mode: Inappropriate ioctl for device


Many thanks for any help!!!

---

### Post by Frogs Hair on 2018-02-05
Support question, moved to *General Help. *

---

### Post by xrayed on 2018-02-05
Double post, please close/delete this one, thanks.

---

### Post by deadflowr on 2018-02-05
Thread closed
duplicate here: [https://ubuntuforums.org/showthread.php?t=2384307]("https://ubuntuforums.org/showthread.php?t=2384307")

---

