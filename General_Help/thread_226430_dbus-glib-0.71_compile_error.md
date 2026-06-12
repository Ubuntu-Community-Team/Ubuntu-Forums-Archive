---
title: "dbus-glib-0.71 compile error"
date: 2006-07-31
forum: General Help
---

### Post by kadane|R| on 2006-07-31
Hi everyone..

I'm trying to compile dbus-glib-0.71 on ubuntu 6.06 runnig xgl-gnome-compiz
I have intel p2.4 ~750 ram... kernel 2.6.15-23-386

..tried an older version but getting the same resoult

I'm getting the following error:
```
DBUS_TOP_BUILDDIR=.. dbus-send --system --print-reply=literal --dest=org.freedesktop.DBus /org/freedesktop/DBus org.freedesktop.DBus.Introspectable.Introspect > dbus-bus-introspect.xml.tmp && mv dbus-bus-introspect.xml.tmp dbus-bus-introspect.xml
Failed to open connection to system message bus: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: No such file or directory
```

I'm an advanced newbie so be gentle ;-) 

Thanks...

---

