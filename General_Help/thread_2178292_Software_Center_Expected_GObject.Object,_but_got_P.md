---
title: "Software Center: Expected GObject.Object, but got PyCObject error"
date: 2013-10-02
forum: General Help
---

### Post by patso23 on 2013-10-02
Hello, apologies if anyone has posted about this before but I wasn't able to find anything on it.

Recently did an update on 13.04, running gnome shell 3.8, and ever since I've been unable to run software-center or gnome-tweak-tool.

I receive the following error:

> error: XDG_RUNTIME_DIR not set in the environment.2013-10-02 16:35:25,585 - softwarecenter.ui.gtk3.app - INFO - setting up proxy 'None'
2013-10-02 16:35:26,393 - softwarecenter.region - WARNING - failed to use geoclue: 'org.freedesktop.Geoclue.Error.notAvailable: Geoclue master client has no usable Address providers'
2013-10-02 16:35:26,457 - softwarecenter.backend.reviews - WARNING - Could not get usefulness from server, no username in config file
2013-10-02 16:35:26,460 - softwarecenter.plugin - INFO - activating plugin '<module 'webapps_activation' from '/usr/share/software-center/softwarecenter/plugins/webapps_activation.pyc'>'
2013-10-02 16:35:26,467 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/lib/python2.7/dist-packages/gi/importer.py', 51, 'find_module')'
2013-10-02 16:35:26,467 - root - ERROR - Could not find any typelib for LaunchpadIntegration


(software-center:3641): IBUS-WARNING **: The owner of /home/****/.config/ibus/bus is not root!
2013-10-02 16:35:26,525 - softwarecenter.db.pkginfo_impl.aptcache - INFO - aptcache.open()
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


Anyone else experiencing this? I noticed that there is a bug filed on launchpad and it is confirmed, but no one is assigned.

Any help would be appreciated.

---

### Post by wicked circuits on 2013-10-03
I am running into this same issue, I am running ubuntu 13.04, installed gnome-shell, and desktop environment. It didn't work, but now that I've uninstalled it and everything else, it still doesn't work. It must be something the shell install messed with. I will update here if I can get it running again.

---

### Post by jnesset on 2013-10-07
I'm having the same problem. Cannot open software-center, tweak-tool or the apperance-app. Neither can I change the background by right-clicking. I think it happened after I installed Gnome Shell. I uninstalled it because it didn't work properly and then I started to get a lot of crash messages. When uninstalling I also removed these, but I don't think that is what caused the problem (or?):

sudo add-apt-repository ppa:ricotz/testing
sudo add-apt-repository ppa:gnome3-team/gnome3
sudo add-apt-repository ppa:gnome3-team/gnome3-staging

---

