---
title: "How to tell Xorg to re-read xorg.conf config file?"
date: 2008-04-29
forum: General Help
---

### Post by bs0d on 2008-04-29
Hi, I have troubles with xbindkeys+OpenArena: if I start the game my mouse pointer jumps to right bottom corner. I found the xorg.conf entry which responsible for this:

```
Option	"CorePointer"
```

in InputDevice section.

But I need this option to bind custom commands to mouse buttons (I do copy/paste,enter and space with mouse). If I comment out this line and restart X I can play but xbindkeys not working..

I read about bntx but this package is not in repository so I try without bntx.

So I thought may be its possible to change xorg.conf (comment this option out) and re-read config, I try kill -HUP but X close instead.

can somebody give me advice?

thanks

---

### Post by Monicker on 2008-04-29
The only way I know of is do to  CTRL + ALT + BACKSPACE

They key combination will close and restart the X server.

---

### Post by bs0d on 2008-04-29
> CTRL + ALT + BACKSPACE

They key combination will close and restart the X server. 

not, its not what I mean.

In Linux many deamons can reload config file without stop working, simple by sending signal or run command with some paramenters. It works much faster then /etc/init.d/name stop .... start.

for example Apache can be told to re-read configuration files and re-open log files, **without** dropping connections in progress, as currently happens with a -HUP restart.

---

### Post by Monicker on 2008-04-29
You could try this:

[http://ubuntuforums.org/showthread.php?p=4211618]("http://ubuntuforums.org/showthread.php?p=4211618")

---

