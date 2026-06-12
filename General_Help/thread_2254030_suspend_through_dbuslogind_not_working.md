---
title: "suspend through dbus/logind not working"
date: 2014-11-24
forum: General Help
---

### Post by DLGandalf on 2014-11-24
Hi, 

I noticed by using XBMC/Kodie beta3, that suspend is not working, Kodi has changed to use systemd-logind to initiate suspend,  but it isn't working.

I'd like to ask someone with kubuntu  14.04 to check if his/her system *does* successfully suspend and come back when doing:
  ```
qdbus --system org.freedesktop.login1 /org/freedesktop/login1 org.freedesktop.login1.Manager.Suspend 1
```

Note: no sudo!

The only thing I notice in syslog is:
```
Nov 24 12:26:18 hans-laptop console-kit-daemon[650]: GLib-CRITICAL: Source ID 34 was not found when attempting to remove it
```

But I'm not at all sure if this is the reason for the failure to suspend, or something completely unrelated, or just a side effect of a common cause. The PC enters a weird state where some services are shutdown, like NetworkManager, LIRC, etc, but doesn't go to S3

---

