---
title: "Restricted-Manager aborts with segfault"
date: 2007-10-08
forum: General Help
---

### Post by zw0rk on 2007-10-08
I'm using Kubuntu 7.04. After apt-get install restricted-manager, i've tried to run it:
and it segfaults :( Is there a way to fix it?

```

root@desktop:/etc/default# restricted-manager
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/bin/restricted-manager:243: Warning: invalid (NULL) pointer instance
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")
/usr/bin/restricted-manager:243: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")
/usr/bin/restricted-manager:243: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")
/usr/bin/restricted-manager:243: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")
/usr/bin/restricted-manager:243: Warning: value "TRUE" of type `gboolean' is invalid or out of range for property `visible' of type `gboolean'
  xml = gtk.glade.XML("/usr/share/restricted-manager/manager.glade")
/usr/bin/restricted-manager:111: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  theme = gtk.icon_theme_get_default()
/usr/bin/restricted-manager:103: GtkWarning: Screen for GtkWindow not set; you must always set
a screen for a GtkWindow before using the window
  self.dialog.show()
/usr/bin/restricted-manager:103: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_new: assertion `context != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_set_text: assertion `layout != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_set_attributes: assertion `layout != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_set_alignment: assertion `layout != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_set_ellipsize: assertion `PANGO_IS_LAYOUT (layout)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_set_single_paragraph_mode: assertion `PANGO_IS_LAYOUT (layout)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_set_width: assertion `layout != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: PangoWarning: pango_layout_get_extents: assertion `layout != NULL' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: GtkWarning: gtk_icon_theme_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: GtkWarning: gtk_icon_size_lookup_for_settings: assertion `GTK_IS_SETTINGS (settings)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: GtkWarning: Invalid icon size 6

  self.dialog.show()
/usr/bin/restricted-manager:103: GtkWarning: gtk_icon_theme_load_icon: assertion `GTK_IS_ICON_THEME (icon_theme)' failed
  self.dialog.show()
/usr/bin/restricted-manager:103: Warning: g_error_free: assertion `error != NULL' failed
  self.dialog.show()
Segmentation fault (core dumped)

```

---

### Post by zw0rk on 2007-10-08
I'm sorry :) I needed to do Alt+F2 'gksu restricted-manager' :)

---

