---
title: "Commands executed via sudo NOPASSWD can't connect to X"
date: 2007-01-07
forum: General Help
---

### Post by SkyIsFalling on 2007-01-07
Say I have a line in /etc/sudoers which looks like this:

```
alex    ALL=(ALL) NOPASSWD: /usr/bin/gedit, /usr/games/gnometris
```

And I try to sudo those programs from a gnome-terminal, I get this:

```
alex@arf:~$ **sudo /usr/bin/gedit**
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

cannot open display: (null)
Run '/usr/bin/gedit --help' to see a full list of available command line options.
alex@arf:~$ **sudo /usr/games/gnometris**
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gnometris:8659): Gtk-WARNING **: cannot open display
```

If I sudo a program that's not listed in NOPASSWD (ie, where I have to enter in a password) it works fine, and after I do that the NOPASSWD programs work fine too (until I sudo -K). 

I'm guessing it's permissions issue, because if I xhost +local:root everything works fine.

Does anyone know what causes this?

---

### Post by scrooge_74 on 2007-01-07
try gksudo instead of sudo

---

### Post by SkyIsFalling on 2007-01-07
> **scrooge_74 said:**
> try gksudo instead of sudo

D'oh, should have thought of that.

It works, thanks! :)

---

### Post by SkyIsFalling on 2007-01-11
Bumping this because I've come across another box where I get the same behaviour using both sudo and gksudo:

```
alex@xena:~$ sudo /usr/games/gnometris
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified


(gnometris:6127): Gtk-WARNING **: cannot open display:
```

Again, if I gksudo non-NOPASSWD commands and enter a password there's no problem, and again if I xhost +local:root that makes it work too.

Anyone?

---

### Post by scrooge_74 on 2007-01-11
Check if any of this info applies to you 
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

[http://www.ubuntuforums.org/showthread.php?t=334033&page=2](http://www.ubuntuforums.org/showthread.php?t=334033&page=2)

---

