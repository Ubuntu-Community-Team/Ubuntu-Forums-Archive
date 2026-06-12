---
title: "Problems launching Evolution when connected via FreeNX"
date: 2005-03-28
forum: General Help
---

### Post by Darrena on 2005-03-28
When I attempt to launch Evolution when connected via FreeNX it crashes, the message I recieve when I run it from a terminal are:
> 
(evolution:10157): camel-WARNING **: Invalid root: '/home/darren/.evolution/mail/local/Drafts.ibex.index'

(evolution:10157): camel-WARNING **: version: TEXT.000 (TEXT.000)

(evolution:10157): camel-WARNING **: block size: 1024 (1024) OK

(evolution:10157): camel-WARNING **: free: 0 (0 add size < 1024) OK

(evolution:10157): camel-WARNING **: last: 6144 (6144 and size: 1024) BAD

(evolution:10157): camel-WARNING **: flags: unSYNC
Failed to connect to the D-BUS daemon: Unable to determine the address of the message bus
10157: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4029.
This is normally a bug in some application using the D-BUS library.
10157: arguments to dbus_connection_set_watch_functions() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 3320.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...

Does anyone have any ideas?

Thanks!  :)

---

