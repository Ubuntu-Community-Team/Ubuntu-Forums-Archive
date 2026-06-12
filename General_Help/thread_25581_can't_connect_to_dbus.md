---
title: "can't connect to dbus"
date: 2005-04-10
forum: General Help
---

### Post by atomic0x on 2005-04-10
Hi there,

I'm having a problem with the dbus.  None of my applications can connect to it.  I've run /etc/init.d/dbus-1 restart and still nothing connects.  

Here's what happens when I run dbus-monitor (sudo dbus-monitor)
```

signal interface=org.freedesktop.DBus; member=ServiceAcquired; sender=org.freedesktop.DBus
string::1.3
method call interface=org.freedesktop.DBus; member=AddMatch; sender=:1.3
string:type='method_call'
method call interface=org.freedesktop.DBus; member=AddMatch; sender=:1.3
string:type='method_return'
method call interface=org.freedesktop.DBus; member=AddMatch; sender=:1.3
string:type='error'
error name=org.freedesktop.DBus.Error.AccessDenied; sender=org.freedesktop.DBus
string:A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "(unset)" member "(unset)" error name "org.freedesktop.DBus.Error.UnknownMethod" destination ":1.3")
error name=org.freedesktop.DBus.Error.AccessDenied; sender=org.freedesktop.DBus
string:A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "(unset)" member "(unset)" error name "org.freedesktop.DBus.Error.UnknownMethod" destination ":1.3")
error name=org.freedesktop.DBus.Error.AccessDenied; sender=org.freedesktop.DBus
string:A security policy in place prevents this sender from sending this message to this recipient, see message bus configuration file (rejected message had interface "(unset)" member "(unset)" error name "org.freedesktop.DBus.Error.UnknownMethod" destination ":1.3")

```

Access denied?  Does anyone know why this is.  It's the same when I try to start GVM.  It kicks out an error about connecting to the dbus.
```

libhal.c 644 : Error connecting to system bus: Failed to connect to socket /usr/local/var/run/dbus/system_bus_socket: Connection refused

** (gnome-volume-manager:16227): WARNING **: manager.c/1187: failed to initialize HAL!

```

I know it used to work, but I don't know when it stopped.  Can anyone help?

Thanks a bunch in advance

---

### Post by 3david on 2006-04-30
see: [http://www.ubuntuforums.org/showthread.php?t=6500](http://www.ubuntuforums.org/showthread.php?t=6500)

---

