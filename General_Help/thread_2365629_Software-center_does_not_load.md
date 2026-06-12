---
title: "Software-center does not load"
date: 2017-07-08
forum: General Help
---

### Post by Liamdale on 2017-07-08
The software-center stopped loading.  I rarely use the software-center but I would like my OS to operate completely.  I have done extensive web searches and have realized that this is not a rare problem.  All the solutions proposed did not correct the problem. 

> sudo apt-get update
sudo apt-get upgrade
sudo apt-get remove --purge software-center
sudo apt-get upgrade
sudo apt-get install software-center


The software seemed to install but would not load.

I tried to execute the software-center from the terminal and got the following python error description

> 2017-07-08 11:22:41,017 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'2017-07-08 11:22:41,090 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2017-07-08 11:22:41,090 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
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

Unfortunately, I don't understand the error message

If someone has a solution it would be appreciated.

---

### Post by walts48 on 2017-07-09
That would make two of us that would appreciate the solution.

I do have Synaptic Package Manager installed.

---

### Post by wildmanne39 on 2017-07-09
Hello walts48, please start your own thread so you can get the help you need and the person that started this one can too, even though you both seem to have the same problem it could be caused by two different things.

Thanks

---

### Post by Liamdale on 2017-07-09
Seems to be a common problem.  I usually use the apt-get from the terminal, Installing  tarball files with debs and Synaptic but I believe that it is never healthy to have a partly broken OS.  Especially when you don't know why.  I hope we will get an answer to the problem.  It maybe related to Cairo-Dock which was the last application I installed.  I removed it because I was also having problems with LibreOffice.  After removing Cairo-Dock I had to remove LibreOffice and reinstall it.  This last problem seems to be corrected.  I liked the software-center to quickly install an app that I was not sure about and removing easily if I didn't like it.

---

