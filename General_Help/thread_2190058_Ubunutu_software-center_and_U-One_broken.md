---
title: "Ubunutu software-center and U-One broken"
date: 2013-11-25
forum: General Help
---

### Post by hotbelgo on 2013-11-25
I installed some extra python stuff to work with [Google APIs]("https://developers.google.com/api-client-library/python/start/installation") ([COLOR=#007000][FONT=Droid Sans Mono]easy_install --upgrade google-api-python-client[/FONT][/COLOR] was the only command I ran that might have had system wide effects) and now two key Ubuntu apps are broken.

software-center: 

  $ sudo software-center[sudo] password for : 
2013-11-25 17:57:40,766 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-11-25 17:57:44,356 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-11-25 17:57:44,358 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-11-25 17:57:44,529 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-11-25 17:57:44,529 - root - ERROR - Could not find any typelib for LaunchpadIntegration


(software-center:20352): IBUS-WARNING **: The owner of /home/sim/.config/ibus/bus is not root!
2013-11-25 17:57:44,853 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-11-25 17:57:50,524 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/utils.py', 271, 'get_title_from_html')'
2013-11-25 17:57:50,523 - root - WARNING - failed to parse: '<div style="background-color: #161513; width:1680px; height:200px;">
 <div style="background: url('/site_media/exhibits/2013/09/AAMFP_Leaderboard_700x200_1.jpg') top left no-repeat; width:700px; height:200px;"></div>
</div>' ('ascii' codec can't encode character u'\xa0' in position 70: ordinal not in range(128))
2013-11-25 17:57:50,556 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
2013-11-25 17:57:57,769 - softwarecenter.db.utils - INFO - software-center-agent finished with status 0
2013-11-25 17:58:01,058 - softwarecenter.ui.gtk3.widgets.exhibits - WARNING - download failed: '<class 'gi._glib.GError'>', 'Operation not supported'
sim@thuisnet-server:~$ software-center-gtk3
2013-11-25 18:12:04,811 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-11-25 18:12:05,153 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/dbus/proxies.py', 410, '_introspect_error_handler')'
2013-11-25 18:12:05,153 - dbus.proxies - ERROR - Introspect error on com.ubuntu.sso:/com/ubuntu/sso/credentials: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1
Traceback (most recent call last):
  File "/usr/bin/software-center-gtk3", line 130, in <module>
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

It does run using sudo

Ubuntu one
$ ubuntuone-launch 
Traceback (most recent call last):
  File "/usr/bin/ubuntuone-launch", line 69, in <module>
    from twisted.internet import defer
  File "/usr/lib/python2.7/dist-packages/twisted/__init__.py", line 53, in <module>
    _checkRequirements()
  File "/usr/lib/python2.7/dist-packages/twisted/__init__.py", line 40, in _checkRequirements
    raise ImportError(required + ".")
ImportError: Twisted requires zope.interface 3.6.0 or later.


Note that I do in fact have zope interface 4.0.5 form Saucy

---

### Post by hotbelgo on 2014-02-02
It looks as though this was something to do with installing the google_api_client into   /usr/local/lib/python2.7/dist-packages/ as removing it seems to have got things started again. Not sure what i will do when I return to my google projects though....

---

