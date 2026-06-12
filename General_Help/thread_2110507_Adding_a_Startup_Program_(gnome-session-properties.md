---
title: "Adding a Startup Program (gnome-session-properties)"
date: 2013-01-30
forum: General Help
---

### Post by 3246251196 on 2013-01-30
If I wanted to add a start up program but run it after a delay, how would I go about doing it? I am having troubles making my session go into a lock screen on start up, is all.

```
gnome-screensaver-command -l
```
If I add an "autostart" program that runs this in Hardy (8) it does what it should. But in Fedora 16 it ignores this command.

But in **either** of the OS the command
```
sleep x; gnome-screensaver-command
```
```
sleep x && gnome-screensaver-command
```

Do not work in Fedora 16, or Hardy.

I am wondering either: How to insert a delay on an autostart program, or how to tell a login to lock screen on reboot. And the reason for this is that in the **custom.conf** file I have enabled auto-login.

Thanks.

===
[http://forums.fedoraforum.org/showthread.php?t=288170]("http://forums.fedoraforum.org/showthread.php?t=288170http://")
===

---

### Post by cogier on 2013-01-30
Has Hardy got a **Startup Applications?** If so you can put the program you want to start in there.

To create a delay you will need to write a script which you could run from the same place.

---

### Post by 3246251196 on 2013-01-31
> **cogier said:**
> Has Hardy got a **Startup Applications?** If so you can put the program you want to start in there.

To create a delay you will need to write a script which you could run from the same place.

Thanks for the hint, something I should have tried anyway!

The idea was to get this working with Fedora, my works machine.

- load up gnome-session-properties
- navigate to the startup program tab (an equivalent was available in Hardy)
- add a new startup program with the command: ```
gnome-screensaver-command -l
```

This seems to work fine in all editions of Ubuntu I have tried, just not in Fedora.

Anyway, this is all tl;dr ; in summary, if this is what you want but does not get seem to get executed:

- just create a simple script:
```

#!/bin/bash
sleep x
gnome-screensaver-command -l

```
ScriptName.sh

- make it executable with chmod
- load up gnome-session-properties
- navigate to the startup program tab
- add a new startup program with the command: ```
/home/$username/ScriptName.sh
```

Thanks all.

---

