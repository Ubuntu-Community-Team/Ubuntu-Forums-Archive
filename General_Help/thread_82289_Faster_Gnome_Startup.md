---
title: "Faster Gnome Startup"
date: 2005-10-26
forum: General Help
---

### Post by müller on 2005-10-26
i found a script on the wiki pages [here]("https://wiki.ubuntu.com/FasterGnomeStartup?highlight=%28FasterGnomeStartup%29")
that is supose to make login time faster
it's:
> #!/bin/sh (-)
eval `ssh-agent`
gnome-settings-daemon &
gnome-panel &
nautilus -n &
beagled --bg &
gnome-screensaver &
exec metacity

Nat Friedman says on his [blog]("http://nat.org/2005/october/#Keep-It-Simple-Stupid"):
> Login time on my machine, as measured with a stopwatch, has been reduced from 10 seconds to 3 seconds

Since I haven't used scripts, i don't know where should i put this script.:confused: 

Dou you know what to do with it?
And has anybody tried it yet?

---

### Post by fabiand on 2005-10-26
Hey,

try and put thos lines into ~/.xsession ... that shoudl do it :)


- fabiand

---

### Post by müller on 2005-10-26
thanx, it worked it reduced my login time from 30s to 20s

BUT after 3s my desktop died (actualy it didn't recive keybord stroaks and mouse cliks)
i switchet to ctrl+alt+F2
and loged in there.
Next moment I recived muchos messages and a line with kernel panic.

Rebooted, deleted the .xsession and we are back to plain slow login time.

---

### Post by ashrack on 2006-09-21
is this script still usefull in DAPPER days?

---

