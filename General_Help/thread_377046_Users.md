---
title: "Users"
date: 2007-03-05
forum: General Help
---

### Post by godswill65 on 2007-03-05
Finaly got my ubuntu up and running.  Loving it so far.

When I go to access the Users and Groups section it comes up with "You are unable to access this" - insufficient access or some such.

Is there a command line way to access this?

---

### Post by aysiu on 2007-03-05
Can you go to the terminal, paste in this command, and then post the output back here in the thread? ```
gksu users-admin
```

---

### Post by godswill65 on 2007-03-06
Sorry just got home from work..

I typed that into a terminal and got this..

----------------------------------------------------------------------------------------------------

(users-admin:5628): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
5628: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
5628: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(users-admin:5628): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
5628: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
5628: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(users-admin:5628): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
5628: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

---------------------------------------------------------------------------------------------------

then got a msgbox saying "The configuration could not be loaded -- You are not allowed to access the system configuration"



Hope you can shed some light!

---

### Post by aysiu on 2007-03-06
[This thread](http://ubuntuforums.org/showthread.php?p=1934080#post1934080) may help you.

---

