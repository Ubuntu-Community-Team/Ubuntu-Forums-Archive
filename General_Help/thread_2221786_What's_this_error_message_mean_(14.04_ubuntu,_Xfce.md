---
title: "What's this error message mean? (14.04 ubuntu, Xfce desktop)"
date: 2014-05-03
forum: General Help
---

### Post by pretty_whistle on 2014-05-03
[IMG]http://i60.tinypic.com/esugt1.png[/IMG]

After a restart I get the above message.  It appears right after login and before reaching the desktop.

My computer is running perfectly so whatever it means it's not affecting anything.  I'm just wondering what it means.  Does anyone know?

---

### Post by ian-weisser on 2014-05-03
When you login, your login gets assigned a display (X_server).
The display includes a utility that makes those notification bubbles (notify_daemon).
Other applications send notifications to notify_daemon via an internal switchboard called dbus.
Notify_daemon's first act after it's started is to connect to dbus and listen for notifications to draw.
Dbus uses funny-named sockets to exchange data between itself and the other applications.

The error means that when you log in, your X session's notification daemon starts, tries to connect to dbus...and fails.

If you get notification bubbles anyway, then the error can be safely ignored.

---

### Post by sammiev on 2014-05-03
Likely totally incorrect, but I would exit your desktop session without saving and see if that error comes back up on next boot.

---

