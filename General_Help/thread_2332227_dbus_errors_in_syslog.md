---
title: "dbus errors in syslog"
date: 2016-07-29
forum: General Help
---

### Post by David_Partridge on 2016-07-29
I was doing a tail - f /var/log/syslog while installing the 16.04.1 upgrade on my 14.04 server.

I'm seeing lots of entries like :

```
Jul 29 18:27:48 Charon dbus[808]: [system] Unable to reload configuration: Failed to open "/etc/dbus-1/system.conf": No such file or directory
Jul 29 18:27:58 Charon dbus[808]: message repeated 63 times: [ [system] Unable to reload configuration: Failed to open "/etc/dbus-1/system.conf": No such file or directory]
:
Jul 29 18:29:42 Charon dbus[808]: [system] Activating service name='org.freedesktop.ModemManager1' (using servicehelper)
Jul 29 18:29:42 Charon dbus[808]: [system] Activated service 'org.freedesktop.ModemManager1' failed: Failed to setup environment correctly

```

Any guidance on resolving this please (I don't think it's related to the upgrade).

***** Looks like the errors have gone after completing the upgrade. ******

TIA 
Dave

---

