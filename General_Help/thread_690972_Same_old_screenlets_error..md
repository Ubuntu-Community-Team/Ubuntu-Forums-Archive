---
title: "Same old screenlets error."
date: 2008-02-08
forum: General Help
---

### Post by wolterh on 2008-02-08
HI. I installed screenlets some hours ago, but I keep getting this error:
```

    screenlets.session.create_session(TestScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 391, in create_session
    session = ScreenletSession(classobj)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 81, in __init__
    self.connect_daemon()
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 86, in connect_daemon
    bus = dbus.SessionBus()
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 218, in __new__
    mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/_dbus.py", line 107, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/var/lib/python-support/python2.5/dbus/bus.py", line 121, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

```

My screenlets-manager is working ok (when ran in console it says DAEMON FOUND!
and some guy around this forums told another dude to write dbus-daemon --session

I did it, but the terminal doesn't give an output.

How can I fix my problem?

PS: I also added the repository, even though I installed via make install method.

---

