---
title: "Launching ununtu software-center in 13.10"
date: 2013-12-28
forum: General Help
---

### Post by deepak.s_singh on 2013-12-28
Hi,
I newly install ubuntu 13.10 in dell vostro laptop. When i am trying to launch software-center, its openings for few seconds and automatically its going to close. I also tried in terminal through command "software-center" and below mentioned logs are comming-

```
deepak@deepak-Vostro-1450:~$ software-center
2013-12-25 09:12:02,875 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-12-25 09:12:03,187 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-12-25 09:12:03,190 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-12-25 09:12:03,197 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-12-25 09:12:03,197 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-12-25 09:12:03,259 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/gi/overrides/GLib.py", line 634, in <lambda>
    return (lambda data: callback(*data), user_data)
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 261, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 105, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 154, in open
    self._list.read_main_list()
SystemError: E:Opening /etc/apt/sources.list - ifstream::ifstream (13: Permission denied)
2013-12-25 09:12:04,449 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1375, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1313, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 227, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 326, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 121, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 255, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 240, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 281, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
```


can anyone please help me for this issue.

Thanks
Deepak Singh

---

### Post by QIII on 2013-12-28
[I]Moved to [B]General Help


[/B][/I]The Ubuntu + 1 sub forum is for discussion of the development version of Ubuntu, which is currently 14.04 Trusty Tahr.

---

### Post by deadflowr on 2013-12-28
Try updating.
Open the dash and find the program "software updater"
Let it run and when it finishes running it's check, look over and install the updates.
when that's done, then try opening the software center.
If this is a new install, you may need to do a restart.

I don't know if this'll actually help, but it's worth a try.

---

