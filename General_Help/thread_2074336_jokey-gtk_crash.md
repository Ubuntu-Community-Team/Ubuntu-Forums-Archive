---
title: "jokey-gtk crash"
date: 2012-10-21
forum: General Help
---

### Post by phoenix455 on 2012-10-21
Hello, 
I've just installed ubuntu 12.04 and i wanted to install nvidia graphic card drivers but when i hit "additional drivers" ubuntu crashes. 

Log from crash : 

(jockey-gtk:6071): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed

(jockey-gtk:6071): Gtk-CRITICAL **: gtk_icon_set_render_icon_pixbuf: assertion `icon_set != NULL' failed
Traceback (most recent call last):
  File "/usr/bin/jockey-gtk", line 418, in <module>
    sys.exit(u.run())
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 468, in run
    self.ui_show_main()
  File "/usr/bin/jockey-gtk", line 94, in ui_show_main
    self.update_tree_model()
  File "/usr/bin/jockey-gtk", line 275, in update_tree_model
    info = self.get_ui_driver_info(h_id)
  File "/usr/lib/python2.7/dist-packages/jockey/ui.py", line 295, in get_ui_driver_info
    info = self.backend().handler_info(handler_id)
  File "/usr/lib/python2.7/dist-packages/dbus/proxies.py", line 145, in __call__
    **keywords)
  File "/usr/lib/python2.7/dist-packages/dbus/connection.py", line 651, in call_blocking
    message, timeout)
dbus.exceptions.DBusException: org.freedesktop.DBus.Python.ValueError: Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/dbus/service.py", line 707, in _message_cb
    retval = candidate_method(self, *args, **keywords)
  File "/usr/lib/python2.7/dist-packages/jockey/backend.py", line 264, in handler_info
    'recommended': str(h.recommended()),
  File "/usr/share/jockey/handlers/nvidia.py", line 130, in recommended
    nd = NvidiaDetection()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 68, in __init__
    self.getData()
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 149, in getData
    driver_version = self.__get_value_from_name(stripped_package_name)
  File "/usr/lib/python2.7/dist-packages/NvidiaDetector/nvidiadetector.py", line 87, in __get_value_from_name
    v = int(name)
ValueError: invalid literal for int() with base 10: 'experimental-304'

---

### Post by phoenix455 on 2012-10-21
Problem solved. I just had to download updates.

---

