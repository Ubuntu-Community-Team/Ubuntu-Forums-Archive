---
title: "pass startup commands to gnome-terminal"
date: 2006-11-14
forum: General Help
---

### Post by mtron on 2006-11-14
Chhers! 

got a question about the gnome-terminal emulator. i wanna run a program from login via the startup sessions. it needs to be called via the gnome terminal, but i want to use a special terminal profile that restarts the app if it ends unexpected.

The profile is already created and labeled "myth"

how would the command for the autostart session look like ?

with xterm it's as simple as running "xterm mythbackend" but i want to use the specified profile.

---

### Post by mtron on 2006-11-22
ist dam easy: 

```
gnome-terminal --window-with-profile=mythbackend 
```

(the profile is set up to run mythbackend automatically and restart it, if it exits)

---

