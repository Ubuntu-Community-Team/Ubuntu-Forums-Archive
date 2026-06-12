---
title: "Sonata isn't working correcty .."
date: 2007-04-30
forum: General Help
---

### Post by PhockouS on 2007-04-30
Hi . I'm new at this forum , so at start I want to say hello to You all : Hello :)

Ok , I've got this problem .

I don't know it's fault of sonata or maybe mpd , one I know is : Sonata can't load to the dbus . 

I'm twisted , because all worked correctly to today . Now sonata is broken .

Maybe somebody can help me ? I'm googling all the time , and noone have the same problem ..

Regards



phockous@funKy:~$ sonata
/usr/lib/python2.5/site-packages/sonata.py:57: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
import egg.trayicon
Taglib and tagpy not found, tag editing support disabled.
/usr/lib/python2.5/site-packages/sonata.py:5406: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

retval = dbus.dbus_bindings.bus_request_name(session_bus.ge t_connection(), "org.MPD.Sonata", dbus.dbus_bindings.NAME_FLAG_DO_NOT_QUEUE)
/var/lib/python-support/python2.5/dbus/_dbus.py:851: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

import dbus.dbus_bindings as m
Po&#322;&#261;czenie z sesj&#261; D-BUS nieudane: Niemo&#380;liwe okre&#347;lenie adresu magistrali wiadomo&#347;ci (spróbuj uzyska&#263; pomoc "man dbus-launch" i "man dbus-deamon")

---

### Post by Dybber on 2007-06-13
I just got exactly the same problem, but I can say that it isn't mpd, I can use it with mpc as interface. The error messsage is almost the same as yours, only the language of the last 2 lines is different, as far as I can tell.


```
/usr/lib/python2.5/site-packages/sonata.py:57: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon
Taglib and tagpy not found, tag editing support disabled.
/usr/lib/python2.5/site-packages/sonata.py:5406: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  retval = dbus.dbus_bindings.bus_request_name(session_bus.get_connection(), "org.MPD.Sonata", dbus.dbus_bindings.NAME_FLAG_DO_NOT_QUEUE)
/var/lib/python-support/python2.5/dbus/_dbus.py:851: DeprecationWarning: The dbus_bindings module is deprecated and will go away soon.

dbus-python 0.80 provides only a partial emulation of the old
dbus_bindings, which was never meant to be public API.

Most uses of dbus_bindings are applications catching the exception
dbus.dbus_bindings.DBusException. You should use dbus.DBusException
instead (this is compatible with all dbus-python versions since 0.40.2).

If you need additional public API, please contact the maintainers via
<dbus@lists.freedesktop.org>.

  import dbus.dbus_bindings as m
Sonata failed to connect to the D-BUS session bus: Unable to determine the address of the message bus (try 'man dbus-launch' and 'man dbus-daemon' for help)
```

---

### Post by blessed on 2007-07-28
does anybody know, who to install tagpy on ubuntu 7.04 (feisty)?

---

