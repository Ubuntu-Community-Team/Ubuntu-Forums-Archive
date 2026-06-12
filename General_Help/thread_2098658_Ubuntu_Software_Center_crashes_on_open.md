---
title: "Ubuntu Software Center crashes on open"
date: 2012-12-27
forum: General Help
---

### Post by skellss on 2012-12-27
When I try to open USC it immediately closes.

opening from terminal provides the following output:
```

xubuntu:~$ software-center
2012-12-27 21:17:02,729 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2012-12-27 21:17:02,734 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2012-12-27 21:17:03,425 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2012-12-27 21:17:03,434 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-12-27 21:17:03,434 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2012-12-27 21:17:03,469 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2012-12-27 21:17:03,472 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2012-12-27 21:17:04,155 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2012-12-27 21:17:04,155 - root - ERROR - Could not find any typelib for Gst

** (software-center:14268): WARNING **: Failed to load shared library 'libwebkitgtk-3.0.so.0' referenced by the typelib: libwebkitgtk-3.0.soso: cannot open shared object file: No such file or directory
/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py:42: Warning: cannot retrieve class for invalid (unclassed) type `void'
  self.webkit = WebKit.WebView()
Traceback (most recent call last):
  File "/usr/bin/software-center", line 182, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1387, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1325, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 151, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 139, in init_view
    SoftwarePane.init_view(self)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/softwarepane.py", line 161, in init_view
    self.cache)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 884, in __init__
    self._layout_page()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/appdetailsview.py", line 1219, in _layout_page
    self.videoplayer = VideoPlayer()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/widgets/videoplayer.py", line 42, in __init__
    self.webkit = WebKit.WebView()
TypeError: could not get a reference to type class


```

I have tried reinstalling USC and libwebkitgtk-3.0
I have no idea what to do, please help me...

---

### Post by ibjsb4 on 2012-12-27
What happens if you try to update in terminal, get any errors?

```
sudo apt-get update
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by skellss on 2012-12-27
Like I said above, when I run it through the terminal is says I'm missing that library.

---

