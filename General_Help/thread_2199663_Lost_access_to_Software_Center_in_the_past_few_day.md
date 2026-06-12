---
title: "Lost access to Software Center in the past few days"
date: 2014-01-15
forum: General Help
---

### Post by fr33z0n3r on 2014-01-15
It is no longer able to open.  The cursor simply spins and then nothing happens.  I've rebooted and that had no effect.

I've made no changes associated with Software Center recently, just installed some python related apps (incl python-pip and python-setuptools) via it a few days ago.  I've been applying updates as they popup.  Software Updater is able to run fine.

Ubuntu 13.04

Any ideas?

---

### Post by jeanjd63 on 2014-01-15
Hello.
Could you try this command :
[B]software-center
[/B]What is the return ?

---

### Post by fr33z0n3r on 2014-01-15
Thanks for that!  Turns out it is my Ubuntu One config.  I disable it.  How do I get it reenabled? lol.  I was trying to disable the file sharing component, not the entire functionality!

well, to be clear, here is the error info.  I'm thinking my python changes have horked it.

```
user:~$ software-center
2014-01-15 07:30:16,218 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2014-01-15 07:30:16,299 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2014-01-15 07:30:16,299 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 141, in find_oauth_token_sync
    sso.find_credentials()
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 75, in find_credentials
    self.proxy.find_credentials(self.appname, self._get_params())
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
```




And launching the Ubuntu One preferences app gives:

```
$ ubuntuone-control-panel-qt
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-control-panel-qt", line 29, in <module>
    from ubuntuone.controlpanel.gui.qt import main
  File "/usr/lib/python2.7/dist-packages/ubuntuone/__init__.py", line 16, in <module>
    __import__('pkg_resources').declare_namespace(__name__)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2823, in <module>
    add_activation_listener(lambda dist: dist.activate())
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 710, in subscribe
    callback(dist)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2823, in <lambda>
    add_activation_listener(lambda dist: dist.activate())
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2255, in activate
    self.insert_on(path)
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2362, in insert_on
    self.check_version_conflict()
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2401, in check_version_conflict
    for modname in self._get_metadata('top_level.txt'):
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 2249, in _get_metadata
    for line in self.get_metadata_lines(name):
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1219, in get_metadata_lines
    return yield_lines(self.get_metadata(name))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1211, in get_metadata
    return self._get(self._fn(self.egg_info,name))
  File "/usr/lib/python2.7/dist-packages/pkg_resources.py", line 1326, in _get
    stream = open(path, 'rb')
IOError: [Errno 13] Permission denied: '/usr/local/lib/python2.7/dist-packages/google_api_python_client-1.2-py2.7.egg/EGG-INFO/top_level.txt'
```

---

### Post by jeanjd63 on 2014-01-15
You can try :
**sudo  software-center**

---

### Post by fr33z0n3r on 2014-01-15
This works, but i'd like the regular access of course. any ideas?

---

