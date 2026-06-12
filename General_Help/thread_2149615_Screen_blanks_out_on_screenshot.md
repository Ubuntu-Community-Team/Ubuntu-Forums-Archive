---
title: "Screen blanks out on screenshot"
date: 2013-05-29
forum: General Help
---

### Post by 96th on 2013-05-29
Hi. I've got a funny issue here that I cannot quite describe. Sometimes, when I want to take a screenshot (using the built in screenshot tool or Screen Cloud) the screen just blanks out. The first tool produces a completely white screenshot and the second allows me to select an area, but the only thing that shows below it is a white screen with the shadow of the notification bar. This happens seemingly at random, and then stays like this until I reboot. I can't really submit a bug cause I've got no idea what the hell is happening and what package this is happening in etc.

---

### Post by ibjsb4 on 2013-05-29
I assume this is gnome-screenshot.  Try reinstalling it.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:
```
sudo apt-get install --reinstall gnome-screenshot
```

This could also be an all together different problem.  You may want to try another screenshot tool to see how it works.  Maybe shutter.

```
sudo apt-get install shutter
```

---

### Post by 96th on 2013-05-29
Reinstalling gnome-screenshot caused the problem to occur and shutter experiences the same problem.

---

### Post by ibjsb4 on 2013-05-29
Open gnome-screenshot using the terminal.

```
gnome-screenshot
```

Get any errors?

---

### Post by 96th on 2013-05-29
Nope :/ I think it's more something to do with the display server than gnome-screenshot actually.

Edit: I ended up reporting a bug: [https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/1194509](https://bugs.launchpad.net/ubuntu/+source/gnome-screenshot/+bug/1194509)

---

