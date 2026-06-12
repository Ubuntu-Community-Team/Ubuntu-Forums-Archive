---
title: "False when start software-center on ubuntu 14.04 LTS"
date: 2014-10-15
forum: General Help
---

### Post by andyhuynh on 2014-10-15
[COLOR=#000000]I'm having problems when using software-center on ubuntu 14:04. In fact this is rarely used to, but that does not fix bugs naturally be annoyed again. 
Their installed some python lib for software-finished, start at center on the Dash is not. command line to start with the following error:
```
/usr/share/software-center$ ./software-center
2014-09-05 16:50:50,195 - softwarecenter.ui.gtk3.app - ERROR - could not initiate dbus
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1250, in setup_dbus_or_bring_other_instance_to_front
    bus = dbus.SessionBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 211, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-qQrifZ8MYA: Connection refused
2014-09-05 16:50:50,334 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
Traceback (most recent call last):
  File "./software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 140, in find_oauth_token_sync
    sso = self. _get_login_backend_and_connect()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 132, in _get_login_backend_and_connect
    _(SOFTWARE_CENTER_SSO_DESCRIPTION))
  File "/usr/share/software-center/softwarecenter/backend/login.py", line 80, in get_login_backend
    sso_class = LoginBackendDbusSSO(window_id, appname, help_text)
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 46, in __init__
    self.bus = dbus.SessionBus()
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 211, in __new__
    mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/_dbus.py", line 100, in __new__
    bus = BusConnection.__new__(subclass, bus_type, mainloop=mainloop)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 122, in __new__
    bus = cls._new_for_bus(address_or_type, mainloop=mainloop)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoServer: Failed to connect to socket /tmp/dbus-4LxDvcQY7L: Connection refused
```

[/COLOR]

Who knows please help me!

---

