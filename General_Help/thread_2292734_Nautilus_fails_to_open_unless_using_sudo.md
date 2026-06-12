---
title: "Nautilus fails to open unless using sudo"
date: 2015-08-30
forum: General Help
---

### Post by EssG on 2015-08-30
Trying to start file manager, and it no longer works. I  just get a spinner and then nothing. When I run it in the terminal I get the following error:

```

(nautilus:25538): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:25538): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Could not register the application: Timeout was reached

(nautilus:25538): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:25538): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:25538): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

```

If I do sudo nautlius, it will open, but if I do it from a terminal I see this output:

```

(nautilus:25954): Gtk-WARNING **: Failed to register client: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

** (nautilus:25954): CRITICAL **: Another desktop manager in use; desktop window won't be created

```

Help would really be appreciated, I have no idea what caused this.

---

