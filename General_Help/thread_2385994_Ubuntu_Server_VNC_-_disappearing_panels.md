---
title: "Ubuntu Server VNC - disappearing panels"
date: 2018-02-27
forum: General Help
---

### Post by przemek7 on 2018-02-27
I have Ubuntu 17.10 + vnc server. After some time, top and bottom panels disappears (shown on picture):

[IMG]https://zapodaj.net/images/781ad678e60da.png[/IMG]

After restarting vnc both panels are visible again, but they disappear after some time (don't know why). Reconnecting to vnc doesn't help, only service restart helps. Screenshot without panels below:

[IMG]https://zapodaj.net/images/486a60e07146c.png[/IMG]

Xstartup file:

```
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &

gnome-session
gnome-panel
gnome-settings-daemon
metacity
nautilus
gnome-terminal
```

---

