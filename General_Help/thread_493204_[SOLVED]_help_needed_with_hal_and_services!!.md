---
title: "[SOLVED] help needed with hal and services!!"
date: 2007-07-05
forum: General Help
---

### Post by spyros71 on 2007-07-05
Hi everybody. While trying to burn a CD the pc crashed. Since then I get an error message that Hal can't be loaded. I know that this is because dbus is messed up. But I also get an other strange result. When I try to activate dbus through services admin I receive the following error message:

spyros@Workstation:~$ services-admin

(services-admin:10734): Liboobs-WARNING **: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
10734: arguments to dbus_connection_add_filter() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4379.
This is normally a bug in some application using the D-Bus library.
10734: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

(services-admin:10734): Liboobs-CRITICAL **: run_message: assertion `oobs_session_get_connected (priv->session)' failed
10734: arguments to dbus_connection_send_with_reply_and_block() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 2873.
This is normally a bug in some application using the D-Bus library.

Services-admin fails to start.

Can someone help me with this one, or show me a way to fix DBUS?? 


Thanks in advance.

---

### Post by computer_user_au on 2007-07-07
Hi, Had the same problem... check out this link: [http://ubuntuforums.org/showthread.php?t=289654&highlight=services-admin]("http://ubuntuforums.org/showthread.php?t=289654&highlight=services-admin")
Worked for me...  :)

---

