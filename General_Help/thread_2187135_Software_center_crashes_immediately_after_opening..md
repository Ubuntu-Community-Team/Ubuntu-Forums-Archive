---
title: "Software center crashes immediately after opening."
date: 2013-11-11
forum: General Help
---

### Post by jonathandshaggard on 2013-11-11
It just opens, spins twice, and closes. I've re-installed several times, tried rebooting, and as I've only been using linux for three weeks, my knowledge is exhausted. Sorry if this is a repost. Heres what happens in terminal:```
 software-center

(software-center:28999): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:756:1: Expected semicolon


(software-center:28999): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:776:0: Expected a valid selector


(software-center:28999): Gtk-WARNING **: Theme parsing error: button.css:150:14: Not using units is deprecated. Assuming 'px'.


(software-center:28999): Gtk-WARNING **: Theme parsing error: button.css:150:14: Junk at end of value


(software-center:28999): Gtk-WARNING **: Theme parsing error: granite-widgets.css:144:14: Not using units is deprecated. Assuming 'px'.


(software-center:28999): Gtk-WARNING **: Theme parsing error: granite-widgets.css:144:16: Not using units is deprecated. Assuming 'px'.


(software-center:28999): Gtk-WARNING **: Theme parsing error: granite-widgets.css:144:22: Not using units is deprecated. Assuming 'px'.


(software-center:28999): Gtk-WARNING **: Theme parsing error: toolbar.css:110:13: Not using units is deprecated. Assuming 'px'.


(software-center:28999): Gtk-WARNING **: Theme parsing error: toolbar.css:110:13: Junk at end of value
2013-11-10 21:45:10,671 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-11-10 21:45:10,674 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-11-10 21:45:10,925 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file


** (software-center:28999): CRITICAL **: failed to load icon 'lpi-translate': Error opening file: No such file or directory
2013-11-10 21:45:10,966 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-11-10 21:45:10,968 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 176, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1422, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1352, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 154, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 171, in init_view
    self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 238, in __init__
    self.build(desktopdir)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 511, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 273, in _build_homepage_view
    self._append_recommended_for_you()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/catview_gtk.py", line 481, in _append_recommended_for_you
    self.recommended_for_you_panel = RecommendationsPanelLobby(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/recommendations.py", line 160, in __init__
    self._try_sso_login()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/recommendations.py", line 224, in _try_sso_login
    self.RECOMMENDATIONS_OPT_IN_TEXT)
  File "/usr/share/software-center/softwarecenter/backend/login_sso.py", line 164, in get_sso_backend
    sso_class = LoginBackendDbusSSO(window_id, appname, help_text)
  File "/usr/share/software-center/softwarecenter/backend/login_sso.py", line 48, in __init__
    'com.ubuntu.sso', '/com/ubuntu/sso/credentials')
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 241, in get_object
    follow_name_owner_changes=follow_name_owner_changes)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 248, in __init__
    self._named_service = conn.activate_name_owner(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 180, in activate_name_owner
    self.start_service_by_name(bus_name)
  File "/usr/lib/python2.7/dist-packages/dbus/bus.py", line 278, in start_service_by_name
    'su', (bus_name, flags)))
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Error.Spawn.ChildExited: Process /usr/lib/ubuntu-sso-client/ubuntu-sso-login exited with status 1



```
Thanks for any help.

Edit: Fixed with [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_9_Ubuntu_Software_Center_fails_to_open](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure#Step_9_Ubuntu_Software_Center_fails_to_open)

---

### Post by sanderj on 2013-11-11
Did you Google the last line?

It leads to [http://askubuntu.com/questions/294180/broke-my-software-center-cache](http://askubuntu.com/questions/294180/broke-my-software-center-cache)

---

### Post by jonathandshaggard on 2013-11-11
My .cache folder is on the same drive, although it does run in sudo. When I tried the lest step I get ```
chown: cannot access `/mnt/data/.cache': No such file or directory
```

---

