---
title: "Odd Error when Running FINCH"
date: 2007-10-21
forum: General Help
---

### Post by trmentry on 2007-10-21
I get some odd errors when running Finch in Gutsy.  

I have a fresh install and did a apt-get install finch  

Once it was done, I get this when I run it.

```

process 4873: D-Bus library appears to be incorrectly set up; failed to read machine uuid: Failed to open "/var/lib/dbus/machine-id": No such file or directory
See the manual page for dbus-uuidgen to correct this issue.
 libnm_glib_dbus_init: error, org.freedesktop.DBus.Error.FileNotFound raised:
Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

```

When I try and do a man dbus-uuidgen I get no man entry found.

It spews this for a bit, but doing alt-l to redraw the screen seems to make it go away. ;)

This is on server in a vmware machine, so not sure if that is the cause or not.

Any pointers?

Thanks

---

### Post by trmentry on 2007-10-25
Anyone?

---

### Post by onlinenow on 2007-12-01
i've got the same error today. have u got any solution to this? any body here~~:confused:

i got the problem when i'm trying to use libpurple library and i'm using ubuntu server on VMware as well!

---

### Post by onlinenow on 2007-12-02
got it, apt-get install dbus is needed and then run dbus-uuidgen --enabled

---

