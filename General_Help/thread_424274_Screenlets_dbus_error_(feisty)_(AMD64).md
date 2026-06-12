---
title: "Screenlets dbus error (feisty) (AMD64)"
date: 2007-04-26
forum: General Help
---

### Post by Yaffle on 2007-04-26
Hello,
I have spent ages looking for a working/decent widgets applicaton I found Screenlets I installed it fine, It ran ok. then just recently I get this error.

[PHP]dale@dale-desktop:~$ screenletsd add Notes[/PHP]
[PHP]

Screenletsd v0.0.1 | (c) RYX (Rico Pfaus) 2007 | released under the GPL
Traceback (most recent call last):
  File "/usr/local/share/screenlets/add-screenlet.py", line 16, in <module>
    '/org/freedesktop/Screenlets')
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 410, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 230, in __init__
    _dbus_bindings.UInt32(0))
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 169, in __call__
    reply_message = self._connection.send_message_with_reply_and_block(message, timeout)
dbus.DBusException: org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.Screenlets was not provided by any .service files
[/PHP]

**Does anyone know a solution to this?**

---

### Post by Yaffle on 2007-04-26
I done some research and it some think to do with my python version. does anyone know how i can get it to run in an older version?

---

