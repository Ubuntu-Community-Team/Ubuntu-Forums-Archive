---
title: "Software center does not work on my 12.10"
date: 2013-03-22
forum: General Help
---

### Post by madeng84 on 2013-03-22
I have a problem with my ubuntu software center (Ubuntu 12.10)
It does not work
I reinstalled it but no changes..

this is the problem
(running software-center from terminal)

xxx@xxx-laptop:~$ software-center
2013-03-22 23:11:57,448 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-03-22 23:11:57,456 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-03-22 23:11:57,651 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2013-03-22 23:11:57,651 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 337, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 139, in find_oauth_token_sync
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

Can u help me?

---

### Post by sanderj on 2013-03-22
did you google "dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:"?

Furhermore: I would run from the commandline:

sudo apt-get update
sudo apt-get upgrade

HTH

---

### Post by madeng84 on 2013-03-23
> **sanderj said:**
> did you google "dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:"?

today yes, and so i asked help here([https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1085425?comments=all](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/1085425?comments=all))....
it seems to be a problem with python modules, problems between python modules end ubuntu one..

 HTH

> **sanderj said:**
> 
Furhermore: I would run from the commandline:

sudo apt-get update
sudo apt-get upgrade
 HTH

This would be the next step

Tnx :D

---

