---
title: "x11vnc service"
date: 2019-04-27
forum: General Help
---

### Post by Headcase_Fargone on 2019-04-27
I'm having trouble getting x11vnc to run as a service in Ubuntu 18.04.  If I run it manually I'm able to connect from remote machines, but when running with the same parameters using systemctl I get the following:

xauth: unable to generate an authority file name
-auth guess: failed for display=':0'

Command the service is running:

/usr/bin/x11vnc -display :0 -auth guess -forever -loop -noxdamage -repeat -rfbauth /etc/x11vnc.passwd -rfbport 5900 -shared

---

