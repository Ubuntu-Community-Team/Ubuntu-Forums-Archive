---
title: "synaptic error; error exit status 139"
date: 2007-08-09
forum: General Help
---

### Post by AmonSacha on 2007-08-09
I am using the latest stable distro with everything updated.

This error has been happening since I tried to install the totem-xine and it attempted to remove totem-gstreamer.

I have tried dpkg --configure -a
I have tried removing and reinstalling the package
ignore the totem mozilla error, that was just what i also tried to install at the same time.

Setting up totem-gstreamer (2.18.1-0ubuntu3) ...

(update-desktop-database:10972): GLib-CRITICAL **: g_key_file_get_string_list: assertion `group_name != NULL' failed
Segmentation fault (core dumped)
dpkg: error processing totem-gstreamer (--configure):
 subprocess post-installation script returned error exit status 139
dpkg: dependency problems prevent configuration of totem-mozilla:
 totem-mozilla depends on totem-xine (>= 2.18.1-0ubuntu3) | totem-gstreamer (>= 2.18.1-0ubuntu3); however:
  Package totem-xine is not installed.
  Package totem-gstreamer is not configured yet.
dpkg: error processing totem-mozilla (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 totem-gstreamer
 totem-mozilla

If any other log files are need just give me a path and name and I will post it
Should I file a bug report?

Help is greatly appreciated!

Thanks
Amon

---

