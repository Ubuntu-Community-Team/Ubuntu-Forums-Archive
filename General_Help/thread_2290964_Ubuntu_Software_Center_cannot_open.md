---
title: "Ubuntu Software Center cannot open"
date: 2015-08-16
forum: General Help
---

### Post by qzf368 on 2015-08-16
Software Center has been broken a few months, and I searched all solutions but could not work on my Ubuntu 14.04. I've tried uninstalling then reinstalling from  Terminal, but no success. 
I try to follow the steps on the [http://ubuntuforums.org/showthread.php?t=2274349](http://ubuntuforums.org/showthread.php?t=2274349), but still fails.
If I try opening it from the terminal by entering "software-center" I  end up getting the following terminal Message:

2015-08-17 10:45:28,213 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2015-08-17 10:45:53,246 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2015-08-17 10:45:53,246 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Traceback (most recent call last):
  File "/usr/bin/software-center", line 130, in <module>
    app = SoftwareCenterAppGtk3(options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 338, in __init__
    self.icons)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/appmanager.py", line 66, in __init__
    self.oauth_token = helper.find_oauth_token_sync()
  File "/usr/share/software-center/softwarecenter/backend/ubuntusso.py", line 141, in find_oauth_token_sync
    sso.find_credentials()
  File "/usr/share/software-center/softwarecenter/backend/login_impl/login_sso.py", line 74, in find_credentials
    self.proxy.find_credentials(self.appname, self._get_params())
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 70, in __call__
    return self._proxy_method(*args, **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by imnmfotmal on 2015-09-23
i am facing the same issue. I just reinstalled ubuntu 14.04 and software center was working fine till now.

---

