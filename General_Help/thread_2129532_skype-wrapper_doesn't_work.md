---
title: "skype-wrapper doesn't work"
date: 2013-03-26
forum: General Help
---

### Post by gamblor01 on 2013-03-26
I (unfortunately) have to install Skype for use at work.  I installed it and was annoyed that the UI is horribly inconsistent with Unity so I did a few google searches and ran across the skype-wrapper package.  I installed it and authorized it, etc. but even after rebooting my machine, deleting ~/.Skype, dragging /usr/share/applications/skype-wrapper.desktop to my launcher, and so on...it just doesn't work.  Notifications are not native Unity notifications, the quicklists are missing from the launcher (in fact, I don't even see any quicklists defined in /usr/share/applications/skype-wrapper.desktop which might explain why they don't show up when I right-click!!), badges don't show up on the launcher icon, and possibly more?

I have already done some google searches and neither of these helped:

[http://ubuntuforums.org/showthread.php?t=2101342](http://ubuntuforums.org/showthread.php?t=2101342)

[http://askubuntu.com/questions/235777/ubuntu-12-10-skype-4-1-cannot-properly-run-wrapper](http://askubuntu.com/questions/235777/ubuntu-12-10-skype-4-1-cannot-properly-run-wrapper)




Maybe this bug is affecting me?

[https://bugs.launchpad.net/skype-wrapper/+bug/1052141](https://bugs.launchpad.net/skype-wrapper/+bug/1052141)




I tried running the python command directly (what /usr/bin/skype-wrapper executes) and it seems to suggest that the wrapper is controlling things, and then I guess polling for messages/status updates/transfers every second or so?  Here is the output:

```

$ python /usr/share/skype-wrapper/skype-wrapper.py
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
Starting skype-wrapper
/usr/lib/python2.7/dist-packages/gobject/constants.py:24: Warning: g_boxed_type_register_static: assertion `g_type_from_name (name) == 0' failed
  import gobject._gobject
INFO: Initializing Skype API
INFO: Starting Skype
INFO: Waiting for Skype Process
`menu_proxy_module_load': skype: undefined symbol: menu_proxy_module_load


(skype:16217): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': skype: undefined symbol: menu_proxy_module_load


(skype:16217): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': skype: undefined symbol: menu_proxy_module_load


(skype:16217): Gtk-WARNING **: Failed to load type module: (null)


`menu_proxy_module_load': skype: undefined symbol: menu_proxy_module_load


(skype:16217): Gtk-WARNING **: Failed to load type module: (null)


INFO: Attaching skype-wrapper to Skype process
INFO: Attached complete
INFO: Initializing online status for users
INFO: We are offline
INFO: We are offline
INFO: We are offline
INFO: Checking unread messages
INFO: Checking online status changing users
INFO: Checking online presence
INFO: Checking file transfers
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running
INFO: Checking online presence
INFO: Check if Skype instance is running

```






Here is all of the version information of what I have installed.  Any ideas?

```

$ dpkg -l | grep skype
ii  python-skype                                1.0.32.0-1~quantal1                               all          Skype API wrapper for Python
ii  skype                                       4.1.0.20.0-0ubuntu0.12.04.2                       i386         client for Skype VOIP and instant messaging service
ii  skype-bin                                   4.1.0.20.0-0ubuntu0.12.04.2                       i386         client for Skype VOIP and instant messaging service - binary files
ii  skype-wrapper                               0ubuntu6.5.2~quantal7                             all          Integrate Skype with Unity

```

---

### Post by gamblor01 on 2013-04-09
Oddly enough this just magically started working.  I guess it was after I logged out or maybe after I rebooted?  I'm not really sure but it seems to work fine now so I'm marking this solved.

---

