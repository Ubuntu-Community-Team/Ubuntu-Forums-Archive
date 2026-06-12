---
title: "[Ubuntu] X11 VNC unable to reconnect after timeout"
date: 2016-12-06
forum: General Help
---

### Post by sf23103 on 2016-12-06
I have recently installed Ubuntu 14.04 for the first time.  I installed X11 VNC and have been accessing it via my Mac (Screen Sharing - VNC).  It is working great, except that if the connection times out due to inactivity, I cannot get back in. I attempt to reconnect, and it prompts for a password, but then just spins and never connects.

Since this is now a headless machine, the only way I can get back in is to pull the power in person and reboot!

Does anyone have any suggestions?  One idea I had was to figure out how to change the timeout setting and set it to something extreme.

---

### Post by steeldriver on 2016-12-06
What parameters / options are you invoking x11vnc with? in particular the -forever and/or -once flags

---

### Post by sf23103 on 2016-12-06
Thanks for the reply.  I'm using:

/usr/bin/x11vnc -xkb -auth /var/run/lightdm/root/:0 -noxrecord -noxfixes -noxdamage -rfbauth /etc/x11vnc.pass -forever -bg -rfbport 5900 -o /var/log/x11vnc.log

---

### Post by sf23103 on 2016-12-07
I added '-share' and so far so good.  I'll report back if it doesn't work.  Of course I'll take better suggestions if anyone has any.

---

