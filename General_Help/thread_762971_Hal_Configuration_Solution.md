---
title: "Hal Configuration Solution"
date: 2008-04-22
forum: General Help
---

### Post by samichx on 2008-04-22
Earlier today our office got a bad update across several machines, it was apparently our fault and has happened before (leading to freezes and all kind of nasty stuff.

HAL and the HALD are installed or reinstalled leading to this error:
"subprocess post-installation script returned error exit status 1"

Which is related to this message:
"Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory"

and we came up with one simple and efficient solution to the problem... caused by our messed up DBUS:
"sudo aptitude reinstall dbus"

Then everyone was happy and stuff worked again. The End.

---

