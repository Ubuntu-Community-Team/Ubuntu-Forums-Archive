---
title: "Rythmbox keeps crashing when trying to sync music"
date: 2013-03-27
forum: General Help
---

### Post by West201 on 2013-03-27
Title explains my problems. Whenever I use Rhythmbox to transfer music from my computer to mp3 player, it will suddenly close. In the past it worked fine. I get the following output when running rhythmbox from the terminal. 

```
jesse@jc-ubuntu:~$ rhythmbox

(rhythmbox:2467): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:231:15: Theming engine 'adwaita' not found

(rhythmbox:2467): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:791:16: Theming engine 'adwaita' not found

(rhythmbox:2467): Gtk-WARNING **: Theme parsing error: gtk-widgets.css:1054:16: Theming engine 'adwaita' not found

(rhythmbox:2467): GLib-GIO-CRITICAL **: g_dbus_connection_emit_signal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

(rhythmbox:2467): GLib-GIO-CRITICAL **: g_dbus_connection_emit_signal: assertion `object_path != NULL && g_variant_is_object_path (object_path)' failed

** (rhythmbox:2467): WARNING **: Error calling get_info: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/platform/linux/dbus_interface.py", line 723, in get_info
    return self.service.folders.get_info(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 166, in inner
    result = f(*new_args, **new_kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/logger.py", line 283, in inner
    res = f(*args, **kwargs)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/interaction_interfaces.py", line 717, in get_info
    mdobj = self.fs_manager.get_by_path(path)
  File "/usr/lib/python2.7/dist-packages/ubuntuone-client/ubuntuone/syncdaemon/filesystem_manager.py", line 794, in get_by_path
    mdid = self._idx_path[path]
KeyError: '/home/jesse/.ubuntuone/Purchased from Ubuntu One'


** (rhythmbox:2467): CRITICAL **: syncdaemon_folder_info_get_subscribed: assertion `SYNCDAEMON_IS_FOLDER_INFO (finfo)' failed

```

---

