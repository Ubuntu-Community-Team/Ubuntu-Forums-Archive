---
title: "[SOLVED] Sonata: GTK problem"
date: 2008-01-13
forum: General Help
---

### Post by dbbolton on 2008-01-13
I did have Sonata working fine, but for some reason it no longer does. When I launch it, the tray icon shows up, but the window does not. When I click on the tray icon, nothing happens.

Here is the command line output of launching sonata then clicking on the tray icon:

```

daniel@mephista:~$ sonata
/usr/lib/python2.5/site-packages/sonata.py:57: DeprecationWarning: the module egg.trayicon is deprecated; equivalent functionality can now be found in pygtk 2.10
  import egg.trayicon
Taglib and tagpy not found, tag editing support disabled.
SOAPpy not found, fetching lyrics support disabled.
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
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/sonata.py", line 3767, in trayaction
    if self.window.window.get_state() & gtk.gdk.WINDOW_STATE_WITHDRAWN: # window is hidden
AttributeError: 'NoneType' object has no attribute 'get_state'

```

Any ideas?

---

### Post by vanadium on 2008-01-13
Did you install Sonata from the repos? If that is the case, I suggest you uninstall it using Synaptic, and get the deb file from [www.getdeb.net](www.getdeb.net), which is a mre recent version. I had issues with the repo version a few months ago under Feisty. When reinstalling Gutsy, I immediately installed the getdeb.net version instead of the one in the repos.

---

### Post by dbbolton on 2008-01-13
Yeah, I installed it from the Ubuntu repos. I'll give the newer version a try.

Edit: The deb from getdeb.net gives me a dependency error- libc6- even though I have version 2.5-0ubuntu14 of package libc6 installed.

---

### Post by vanadium on 2008-01-14
I see Ubuntu 7.04 in your signature. You must make sure to download the .deb for your particular distribution.

---

### Post by Tenken on 2008-01-14
I had problems with the tray icon when I first switched to sonata, I had sonata pointing to my music dir, but hadn't run set up the mpd database. Now after any significant changes to my music dir I re-run this command

```
mpd --create-db
```

---

### Post by dbbolton on 2008-01-14
> **vanadium said:**
> I see Ubuntu 7.04 in your signature. You must make sure to download the .deb for your particular distribution.
It seems to be working now. Thanks!

---

