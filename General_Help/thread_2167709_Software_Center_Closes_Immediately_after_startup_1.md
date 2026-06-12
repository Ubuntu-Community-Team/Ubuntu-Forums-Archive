---
title: "Software Center Closes Immediately after startup 13.04"
date: 2013-08-14
forum: General Help
---

### Post by n-matt on 2013-08-14
I'm not sure this is the right place to post this but when I came to my 13.04 machine this morning and tried to start software-center it immediately closed again.

When starting in terminal I get the output below.

2013-08-15 08:09:26,436 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-08-15 08:09:26,875 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-08-15 08:09:26,878 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-08-15 08:09:26,885 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-08-15 08:09:26,885 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-08-15 08:09:26,945 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
2013-08-15 08:09:28,034 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
DatabaseModifiedError: The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation
Traceback (most recent call last):
  File "/usr/bin/software-center", line 183, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1375, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1313, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 150, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 174, in init_view
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
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 82, in __call__
    pkgname = self.db.get_pkgname(doc)
  File "/usr/share/software-center/softwarecenter/db/database.py", line 472, in get_pkgname
    pkgname = doc.get_value(XapianValues.PKGNAME)
xapian.DatabaseModifiedError: The revision being read has been discarded - you should call Xapian::Database::reopen() and retry the operation

---

### Post by Y^2om&amp;#7sgP on 2013-08-15
Not sure if this'll help, but have you tried uninstalling and re-installing the software center?

To uninstall Software Center:
1.
sudo apt-get remove software-center

2.
sudo apt-get autoremove software-center


To re-install Software Center: 
1.
sudo apt-get update

2.
sudo apt-get install software-center

---

### Post by ibjsb4 on 2013-08-15
The second line:

> Could not get usefulness from server

Found this:

[http://askubuntu.com/questions/128244/software-center-empty-no-usefulness-from-server-no-username-in-config-file](http://askubuntu.com/questions/128244/software-center-empty-no-usefulness-from-server-no-username-in-config-file)

---

