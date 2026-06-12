---
title: "unable to perform shutdown authorization required"
date: 2013-09-13
forum: General Help
---

### Post by 316479 on 2013-09-13
On an    Ubuntu 12.04.3 LTS system I recently started getting this message when I tried to shutdown
using the standard shutdown button.

The cure I found was to add a file [FONT=courier new]fixShutdown[/FONT] in the directory /var/lib/polkit-1/localauthority/50-local.d  

The file contains:

```

[Shutting down the system]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.consolekit.system.stop;org.freedesktop.consolekit.system.stop-multiple-users
ResultActive=yes

[Restarting the system]
Identity=unix-group:admin;unix-group:sudo
Action=org.freedesktop.consolekit.system.restart;org.freedesktop.consolekit.system.restart-multiple-users
ResultActive=yes

```

---

