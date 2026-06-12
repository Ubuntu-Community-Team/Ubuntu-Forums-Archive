---
title: "Video Mode Not ....."
date: 2007-07-21
forum: General Help
---

### Post by The Wisedude on 2007-07-21
When I boot in Ubuntu, before the login screen shows up I get a screen like this (REMADE IN GIMP)

[IMG]http://i7.tinypic.com/67od06u.png[/IMG]
PS. I forgot the "e" In "mode" :O.


Why is this?

If this helps I have

ATI X300

Intel Pentium IV 550

---

### Post by bernied on 2007-07-21
That looks to me like a message from your monitor, not from the operating system.

You could try either:
- Hit Ctrl-Alt-F1 - does this give you a terminal? If so, login and
```
sudo dpkg-reconfigure xorg-xserver
```
- Boot into a text terminal and do the same
- Boot into single-user mode and do the same

---

