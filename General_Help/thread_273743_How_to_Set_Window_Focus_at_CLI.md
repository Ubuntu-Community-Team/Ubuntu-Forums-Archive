---
title: "How to Set Window Focus at CLI?"
date: 2006-10-08
forum: General Help
---

### Post by BitTorrentBuddha on 2006-10-08
Hey, I'm trying to make a script to focus my terminal when it's open but open it if it's not. I've got it all worked out so far except the focusing parts, I'm using Beryl, so that might be beneficial (although most likely quite the opposite.)```
#!/bin/bash
if ps -A | grep -e "gnome-terminal" > /dev/null; then
     # insert miracle window focusing command, perhaps something more exotic than bash?
else
     gnome-terminal
fi
```

---

### Post by IYY on 2006-10-09
I'm not sure whether or not this is possible with Metacity (Gnome's default window manager). I know that IceWM has the so called ``icesh'' to do just that.

---

### Post by BitTorrentBuddha on 2006-10-09
I saw that when I was googling around. Unfortunately that doesn't work :(

---

### Post by shizeon on 2006-10-25
I'm looking to do the exact same thing with evolution.  You have any luck finding a way to set windows focus via a script?

---

### Post by shizeon on 2006-10-25
So, found the answer to what we are looking for.  wmctrl.  Looks like it will do exactly what we want and is in the repos.

wmctrl -a gnome-terminal

wmctrl -a evolution

---

