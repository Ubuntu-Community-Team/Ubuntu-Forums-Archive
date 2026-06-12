---
title: "ERROR:dbus"
date: 2019-07-24
forum: General Help
---

### Post by cal12saintclair on 2019-07-24
Hi, I've been using Ubuntu for almost a year now, and haven't experienced many problems. However two days ago I noticed that Software & Updates was closing when I tried to launch it. I had a look online and tried in terminal ~$ software-properties-gtk and got this output 

WARNING:root:could not open file '/etc/apt/sources.list'

WARNING:root:could not open file '/etc/apt/sources.list'


ERROR:dbus.proxies:Introspect error on :1.117:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 172, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.117 was not provided by any .service files


Could anyone help me with trying to fix this. I'm not tech savvy at all so I haven't got a clue whats going wrong. 

Thanks

---

### Post by cal12saintclair on 2019-07-25
Any help at all would be greatly appreciated

---

### Post by eqbal64 on 2019-07-25
> **cal12saintclair said:**
> Hi, I've been using Ubuntu for almost a year now, and haven't experienced many problems. However two days ago I noticed that Software & Updates was closing when I tried to launch it. I had a look online and tried in terminal ~$ software-properties-gtk and got this output 

WARNING:root:could not open file '/etc/apt/sources.list'

WARNING:root:could not open file '/etc/apt/sources.list'


ERROR:dbus.proxies:Introspect error on :1.117:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Message recipient disconnected from message bus without replying
Traceback (most recent call last):
  File "/usr/bin/software-properties-gtk", line 100, in <module>
    app = SoftwarePropertiesGtk(datadir=options.data_dir, options=options, file=file)
  File "/usr/lib/python3/dist-packages/softwareproperties/gtk/SoftwarePropertiesGtk.py", line 172, in __init__
    self.backend.Reload();
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python3/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python3/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name :1.117 was not provided by any .service files


Could anyone help me with trying to fix this. I'm not tech savvy at all so I haven't got a clue whats going wrong. 

Thanks




I am also feel like this

---

