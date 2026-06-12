---
title: "Software center closes unexpectedly"
date: 2013-09-25
forum: General Help
---

### Post by erichbuhler on 2013-09-25
Software center closes unexpectedly and I get the following error; I am using the latest 32-bit Ubuntu version. I tried reinstalling the software center but did not work.

Fontconfig warning: "/etc/fonts/conf.d/50-user.conf", line 14: reading configurations from ~/.fonts.conf is deprecated.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:737:17: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:933:17: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:950:17: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:963:20: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1538:17: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1549:15: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1549:17: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1578:15: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1578:17: Not using units is deprecated. Assuming 'px'.

(software-center:5329): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1637:17: Not using units is deprecated. Assuming 'px'.
2013-09-26 03:07:36,820 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-09-26 03:07:40,294 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-09-26 03:07:40,303 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-09-26 03:07:40,334 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-09-26 03:07:40,333 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-09-26 03:07:40,746 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1375, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1313, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 240, in init_view
    vm.display_page(self, self.Pages.LOBBY, self.state)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 183, in display_page
    pane.enter_page(page, view_state)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 637, in enter_page
    self.display_lobby_page(state)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 652, in display_lobby_page
    self._clear_search()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 559, in _clear_search
    self.searchentry.clear_with_no_signal()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/searchentry.py", line 120, in clear_with_no_signal
    self.handler_block(self._handler_changed)
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GObject.py", line 454, in signal_handler_block
    GObjectModule.signal_handler_block(_get_instance_for_signal(obj), handler_id)
  File "/usr/lib/python2.7/dist-packages/gi/types.py", line 113, in function
    return info.invoke(*args, **kwargs)
TypeError: argument instance: Expected GObject.Object, but got PyCObject

---

### Post by andrew.46 on 2013-09-25
Is Synaptic still available? This might be at least a workaround:

```
sudo apt-get install synaptic
```

---

