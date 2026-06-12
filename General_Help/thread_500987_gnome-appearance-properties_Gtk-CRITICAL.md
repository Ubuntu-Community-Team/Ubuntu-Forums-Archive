---
title: "gnome-appearance-properties: Gtk-CRITICAL"
date: 2007-07-14
forum: General Help
---

### Post by Skellington on 2007-07-14
Hi, everyone.

After upgrading from Ubuntu (amd64) Feisy to Gutsy all seems to works fine except this:

I can't change access # gnome-appearance-properties
I get this Warnings and Criticals and app never starts:



(gnome-appearance-properties:8540): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gnome-appearance-properties:8541): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

(gnome-appearance-properties:8540): Gtk-CRITICAL **: gtk_button_set_image: assertion `GTK_IS_BUTTON (button)' failed

(gnome-appearance-properties:8540): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-appearance-properties:8540): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-appearance-properties:8540): Gtk-CRITICAL **: gtk_tree_view_set_model: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(gnome-appearance-properties:8540): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(gnome-appearance-properties:8540): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(gnome-appearance-properties:8540): capplet-common-CRITICAL **: gconf_peditor_new_tree_view: assertion `tree_view != NULL' failed

(gnome-appearance-properties:8540): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-appearance-properties:8540): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-appearance-properties:8540): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(gnome-appearance-properties:8540): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed
Segmentation fault (core dumped)



Any suggestion?

Thanks in advance!
Jack.

---

