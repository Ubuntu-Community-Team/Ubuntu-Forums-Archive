---
title: "GLib-GObject-CRITICAL"
date: 2015-08-08
forum: General Help
---

### Post by ubu88 on 2015-08-08
Im trying to install baobab and I get these error messages:

> Setting up baobab (3.4.1-1) ...
Processing triggers for menu ...

(gdbus call:18240): GLib-GObject-CRITICAL **: /build/buildd-glib2.0_2.33.12+really2.32.4-5-i386-eISom6/glib2.0-2.33.12+really2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(gdbus call:18240): GLib-GObject-CRITICAL **: /build/buildd-glib2.0_2.33.12+really2.32.4-5-i386-eISom6/glib2.0-2.33.12+really2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(gdbus call:18240): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gdbus call:18240): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(gdbus call:18240): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(gdbus call:18240): GLib-GObject-CRITICAL **: /build/buildd-glib2.0_2.33.12+really2.32.4-5-i386-eISom6/glib2.0-2.33.12+really2.32.4/./gobject/gtype.c:2722: You forgot to call g_type_init()

(gdbus call:18240): GLib-GObject-CRITICAL **: g_type_interface_add_prerequisite: assertion `G_TYPE_IS_INTERFACE (interface_type)' failed

(gdbus call:18240): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(gdbus call:18240): GLib-GObject-CRITICAL **: g_type_add_interface_static: assertion `G_TYPE_IS_INSTANTIATABLE (instance_type)' failed

(gdbus call:18240): GLib-CRITICAL **: g_once_init_leave: assertion `result != 0' failed

(gdbus call:18240): GLib-GObject-CRITICAL **: g_object_new: assertion `G_TYPE_IS_OBJECT (object_type)' failed
**
GLib-GIO:ERROR:/build/buildd-glib2.0_2.33.12+really2.32.4-5-i386-eISom6/glib2.0-2.33.12+really2.32.4/./gio/gdbusconnection.c:6764:get_uninitialized_connection: assertion failed: (ret != NULL)
Aborted



---

