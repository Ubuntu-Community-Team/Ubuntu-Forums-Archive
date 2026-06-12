---
title: "SMB connection issue"
date: 2016-08-22
forum: General Help
---

### Post by waranty922 on 2016-08-22
HI guys, my os is ubuntu 16.04.1 x64.
I have issue connecting to windows shared file and folder i get this error when try to connect using nautilus GUI.
[IMG]https://s3.postimg.org/8i4jokceb/Screenshot_from_2016_08_22_14_24_36.png[/IMG]

when I connect using terminal I get this 

nautilus smb://10.15.0.81


(nautilus:15982): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed


(nautilus:15982): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed


(nautilus:15982): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed


(nautilus:15982): GLib-GObject-WARNING **: invalid (NULL) pointer instance


(nautilus:15982): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

what is solution of this situation ?

---

