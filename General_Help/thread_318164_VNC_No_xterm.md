---
title: "VNC: No xterm"
date: 2006-12-13
forum: General Help
---

### Post by madjon on 2006-12-13
I am running Dapper Drake, 6.06 on a desktop. For whatever reason, when I start vncserver under my username (jon) a blank x-server comes up. No xterm, no nothing. If I start vncserver under root, however, everything works without a problem. My xstartup file is below (same for root and jon) along with part of the log file from starting vncserver under jon.

xstartup
```
#!/bin/sh

xrdb $HOME/.Xresources
xsetroot -solid grey
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
```

Log:
```
xsetroot:  unknown color "grey"
Option --login is no longer supported in this version of gnome-terminal; you might want to create a profile with the desired setting, and use the new --window-with-profile option
Window manager warning: Log level 32: could not find XKB extension.
Could not set mode 0700 on private per-user gnome configuration directory `/home/jon/.gnome2_private/': Operation not permitted

```

---

