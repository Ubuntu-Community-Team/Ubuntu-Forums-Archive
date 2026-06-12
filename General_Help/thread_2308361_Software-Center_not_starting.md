---
title: "Software-Center not starting"
date: 2016-01-02
forum: General Help
---

### Post by hundred1906 on 2016-01-02
Don't know why or when but the Software-Center on my 14.10 desktop has stopped working. Google gives me solutions but none of the fixes I have tried have worked so far.

When I run it from the terminal I get the report below. I think the problem is probably to do with the "dbus proxies" message but after that I am lost. Any help would be appreciated.

I have deleted and re-installed (twice), and have also deleted the directory ~/.cache/sso/ per probably bad advice elsewhere. Also used Synaptic to reinstall it. All leaving the same or similar problem.

```
:~$ software-center
2016-01-02 15:28:26,144 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2016-01-02 15:28:26,303 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2016-01-02 15:28:26,302 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
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
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
```

---

### Post by oldos2er on 2016-01-02
14.10 is no longer supported; you really should upgrade or do a clean install of a supported version e.g. 14.04 LTS or 15.10.

---

### Post by hundred1906 on 2016-01-02
Actually I was wrong my desktop is 14.04. How I got into this problem is through trying to update a vbox machine from 14.10 to 15.10 ... which failed because my vbox needed updating, so I downloaded the update and tried installing via the software-centre ... which will not load.

---

### Post by grahammechanical on 2016-01-02
Each Ubuntu release has its own set of repositories. When a release of Ubuntu reaches the end of its support period then its set of repositories are no longer updated and after a few weeks the repositories are closed, archived and moved to another location.

The result is the same whether we are running Ubuntu from a hard disk install or in a VM. Utilities like Update Manager and Software Centre will throw a hissy fit because they need to access the repositories as they load and the URLs in the software sources lists are now inaccurate.

The work-around is to change the URLs in the software sources list file. But you should know that you cannot upgrade directly from 14.10 to 15.10. You have to upgrade to 15.04 (which is soon to reach end of life) and then upgrade to 15.10.

It might be an interesting experiment to do in a VM. So, here is the link

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Regards

---

### Post by hundred1906 on 2016-01-02
Sorry no, I think forget the VM guest, that is just doing a normal update (whatever version to whateverother version) .. nothing special. My problem is with the software-centre on the  14.04 host, which is up to date.

---

