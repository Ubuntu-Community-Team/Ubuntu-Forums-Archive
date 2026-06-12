---
title: "[SOLVED] How do I disable/re-enable desktop"
date: 2008-06-09
forum: General Help
---

### Post by jlrubin on 2008-06-09
I'm  an enthusiastic linux newbie who is converting an old computer to a file server. I installed xubuntu so I would have a desktop environment while I learned, but now I'm ready to unplug the monitor, keyboard, and mouse, and put the server under my desk with nothing but a power cord and ethernet cable. I plan to manage the box with ssh and webmin.

How do I disable the graphical login screen, x windows, xfce, etc so that it will be easy to re-enable if I want to? I *don't* want to switch to the server version yet, just turn off what I don't need -- the box has just 256MB memory.

---

### Post by ibutho on 2008-06-09
Its quite simple. All you need to do is run a terminal and enter
```
sudo update-rc.d -f gdm remove
```
You can start and X session by running "startx". To re-enable graphical login do
```
sudo update-rc.d gdm defaults
```

---

### Post by cocopuffz on 2008-06-09
well, if Xubuntu is basically the same thing as Ubuntu just running KDE instead of Gnome then I would go:

cnt+alt + f1 to drop into command line then go "sudo /etc/init.d/kde stop"

that should stop kde. To restart it just go "sudo /etc/init.d/kde start"

Is that what you're looking for?

---

### Post by jlrubin on 2008-06-09
That's it?  All of the graphical stuff is started from gdm?

I'll try it.

---

### Post by jlrubin on 2008-06-09
xubuntu uses xfce, not kde.

---

