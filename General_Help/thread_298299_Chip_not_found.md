---
title: "Chip not found"
date: 2006-11-12
forum: General Help
---

### Post by blueturtl on 2006-11-12
After installing and properly configuring lm-sensors I installed Gnome Sensors Applet from the repositories. Everything has worked well ever since until a few days ago when the Gnome Sensors Applet suddenly started displaying error "Chip not found" where it used to display my CPU temperature. I checked the command 'sensors' and it gave me a proper reading so I turned off Gnome Sensors Applet and reloaded it. The temperature was now displayed properly again, but the next time I logged in the same thing happened again! I'm baffled because it worked flawlessly before. Is this a time to file a bug report?

---

### Post by pragmatine on 2006-11-22
Hi, this is a weird one... the problem resides somewhere in the libsensors interface for sensors-applet....Have you recently upgraded the version of lm_sensors? Try removing the file /etc/sensors.conf and then reinstalling lm_sensors so it can be overwritten with a clean version and see if that helps at all.

---

### Post by blueturtl on 2006-11-24
Seems the problem has gone away by itself.
I am not qualified to diagnose this, but if it shows again I will have to look into it more...

---

