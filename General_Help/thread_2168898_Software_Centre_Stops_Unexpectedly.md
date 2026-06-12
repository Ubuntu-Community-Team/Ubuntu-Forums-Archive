---
title: "Software Centre Stops Unexpectedly"
date: 2013-08-19
forum: General Help
---

### Post by ktat on 2013-08-19
Hi, a couple of days ago I tried to install Mudlet before the software center did its thing a warning came up about untrusted packages - I clicked repair.  This process never finished, I don't know why.

The problem now is that whenever I start up the Software Centre  it fails and I get the message that it has had to stop unexpectedly.  Running the Software Centre from the terminal, I get the following output:
> 
2013-08-20 10:29:28,210 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-08-20 10:29:28,222 - softwarecenter.db.database - INFO - open() database: path=None use_axi=True use_agent=True
2013-08-20 10:29:28,974 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-08-20 10:29:28,982 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-08-20 10:29:28,982 - root - ERROR - Could not find any typelib for LaunchpadIntegration
2013-08-20 10:29:29,162 - softwarecenter.ui.gtk3.app - INFO - show_available_packages: search_text is '', app is None.
2013-08-20 10:29:29,166 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()

(software-center:3164): Gdk-CRITICAL **: gdk_error_trap_pop_internal: assertion `trap != NULL' failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 257, in open
    self._cache = apt.Cache(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 102, in __init__
    self.open(progress)
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 145, in open
    self._cache = apt_pkg.Cache(progress)
SystemError: E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/au.archive.ubuntu.com_ubuntu_dists_quantal_universe_i18n_Translation-en, E:The package lists or status file could not be parsed or opened.
2013-08-20 10:29:32,302 - softwarecenter.db.enquire - ERROR - _get_estimate_nr_apps_and_nr_pkgs failed
Traceback (most recent call last):
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 115, in _get_estimate_nr_apps_and_nr_pkgs
    tmp_matches = enquire.get_mset(0, len(self.db), None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'
Traceback (most recent call last):
  File "/usr/bin/software-center", line 182, in <module>
    app.run(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1387, in run
    self.show_available_packages(args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 1325, in show_available_packages
    self.view_manager.set_active_view(ViewPages.AVAILABLE)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/session/viewmanager.py", line 151, in set_active_view
    view_widget.init_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/panes/availablepane.py", line 173, in init_view
    self.cache, self.db, self.icons, self.apps_filter)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 80, in __init__
    self.build()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 324, in build
    self._build_homepage_view()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 119, in _build_homepage_view
    self._append_whats_new()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 253, in _append_whats_new
    whats_new_cat = self._update_whats_new_content()
  File "/usr/share/software-center/softwarecenter/ui/gtk3/views/lobbyview.py", line 238, in _update_whats_new_content
    docs = whats_new_cat.get_documents(self.db)
  File "/usr/share/software-center/softwarecenter/db/categories.py", line 131, in get_documents
    nonblocking_load=False)
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 330, in set_query
    self._blocking_perform_search()
  File "/usr/share/software-center/softwarecenter/db/enquire.py", line 225, in _blocking_perform_search
    matches = enquire.get_mset(0, self.limit, None, xfilter)
  File "/usr/share/software-center/softwarecenter/db/appfilter.py", line 89, in __call__
    if (not pkgname in self.cache and
  File "/usr/share/software-center/softwarecenter/db/pkginfo_impl/aptcache.py", line 277, in __contains__
    return self._cache.__contains__(k)
AttributeError: 'NoneType' object has no attribute '__contains__'

Does anyone know what's going on here and how to fix it?

Thank you.

ps that's not my smilie - I think this computer is playing games with me :confused:

Fixed problem... found this thread solved all
[http://ubuntuforums.org/showthread.php?t=2168390](http://ubuntuforums.org/showthread.php?t=2168390)

---

### Post by bkline on 2013-08-19
> **ktat said:**
> ,,,

ps that's not my smilie - I think this computer is playing games with me :confused:


It's not your computer, it's the forum display software.  In the "Additional Options" box below the editing interface there's a miscellaneous option labeled "Disable smilies in text"; if you check that box you'll avoid having common ASCII character sequences (like colon followed by uppercase P - :P) displayed as graphical icons.

---

