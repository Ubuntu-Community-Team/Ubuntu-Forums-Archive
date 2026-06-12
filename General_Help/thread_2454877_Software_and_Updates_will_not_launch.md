---
title: "Software and Updates will not launch"
date: 2020-12-07
forum: General Help
---

### Post by davehumphreys02186 on 2020-12-07
Have spent some time trying to nail this, to no avail

Have reinstalled software-properties-gtk, nothing

Software and Updates will not launch from Applications, nothing happens when I click on it. Same with Additional Drivers

In terminal, I get:

:~$ sudo software-properties-gtk
ERROR:dbus.proxies:Introspect error on :1.290:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 211, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 72, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 141, in __call__
    return self._connection.call_blocking(self._named_service,
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 652, in call_blocking
    reply_message = self.send_message_with_reply_and_block(
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.290 was not provided by any .service files


Any help would be appreciated.

---

### Post by blackbird34 on 2020-12-08
You reinstalled " software-properties-gtk ", but did you use the purge option? See [https://itsfoss.com/apt-command-guide/](https://itsfoss.com/apt-command-guide/)

That would remove all the configuration that *might* be a problem.

---

