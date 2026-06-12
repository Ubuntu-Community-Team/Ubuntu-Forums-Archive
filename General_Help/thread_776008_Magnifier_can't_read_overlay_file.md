---
title: "Magnifier: can't read overlay file?"
date: 2008-04-30
forum: General Help
---

### Post by GhodMode on 2008-04-30
I select the "Image Overlay" mode in the settings for the Magnifier plugin, but when I initiate the magnifier, I get the simple mode.

Monitoring ~/.xsession-errors file shows me why:```
$ tail -f /home/ghodmode/.xsession-errors | grep compiz
/usr/bin/compiz.real (dbus) - Error: dbus_bus_get error: Failed to execute dbus-launch to autolaunch D-Bus session
/usr/bin/compiz.real (dbus) - Error: InitObject failed
/usr/bin/compiz.real (core) - Error: Couldn't activate plugin 'dbus'
/usr/bin/compiz.real (mag) - Warn: Could not load magnifier overlay image "Gnome/overlay.png"!
/usr/bin/compiz.real (mag) - Warn: Could not load magnifier overlay image "Oxygen/overlay.png"!
/usr/bin/compiz.real (mag) - Warn: Could not load magnifier overlay image "Oxygen/overlay.png"!
```

([color=navy]The dbus messages are unrelated, right?[/color])

So, it looks for the original overlay image once (Gnome/overlay.png), then it looks for the images I've set in the Oxygen subdirectory.  I've confirmed that the images are in place (/usr/share/compiz/Oxygen) and I've tried with and without an absolute path.

**[color=navy]Does anyone have any ideas why this might be happening?[/color]**

Thank you,

--
-- Ghodmode

---

