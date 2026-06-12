---
title: "screen &amp; .bashrc"
date: 2008-06-16
forum: General Help
---

### Post by haaskaa on 2008-06-16
I use screen a lot and want to have it autostart everytime I start a terminal session (Konsole or rxvt-unicode). If I put "exec screen -DR" in my .bashrc I get the effect I want, but with the side-effect that KDE won't log on. I get to the login window but after typing name and passwd nothing happens. How can I have screen start in all terminal sessions without affecting the KDE login ?

---

### Post by justleen on 2008-06-16
how about launching it when yout xterm starts?
eg, start gnome-terminal/xterm with
```
 gnome-terminal -x screen 
xterm -e screen
```

where -x is the command to be executed when the terminal launches.

should work, at least within X

---

