---
title: "How do I get the standard desktop with VNC"
date: 2012-12-03
forum: General Help
---

### Post by hakelm on 2012-12-03
When I log in to my Ubuntu-server over VNC I get an empty desktop with an open X-terminal. I would, however, like to see the the same desktop as I get with a local login with all the features it offers.
How do I accomplish this?
My Ubuntu 11.04 server is running Xtightvnc.
Thankful for any tip.
Håkan

---

### Post by hakelm on 2012-12-03
Solved:
xstartup:
#!/bin/sh
unset SESSION_MANAGER
exec /etc/X11/xinit/xinitrc
[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources


chmod 777 xstartup

start with 
~# vncserver -geometry 1920x1080

---

