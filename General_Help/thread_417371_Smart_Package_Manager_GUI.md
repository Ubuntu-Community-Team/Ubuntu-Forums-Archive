---
title: "Smart Package Manager GUI"
date: 2007-04-21
forum: General Help
---

### Post by Typhon on 2007-04-21
Has anyone tried Smart Package Manager (in GUI mode) in Feisty? On my Kubuntu 7.04 I get the following error when I try to run it from terminal:

(**SOLUTION FOUND** --> see [this post](http://ubuntuforums.org/showthread.php?p=2529985#post2529985).)

```
sudo smart --gui
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:69: GtkWarning: could not open display
  warnings.warn(str(e), _gtk.Warning)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:36: Warning: invalid (NULL) pointer instance
  gtk.Window.__init__(self)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:36: Warning: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
  gtk.Window.__init__(self)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:50: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self._scrollwin = gtk.ScrolledWindow()
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: GtkWarning: gdk_pango_context_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: PangoWarning: pango_context_set_font_description: assertion `context != NULL' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: PangoWarning: pango_context_set_base_dir: assertion `context != NULL' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: PangoWarning: pango_context_set_language: assertion `context != NULL' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: Warning: g_object_unref: assertion `G_IS_OBJECT (object)' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: GtkWarning: gtk_settings_get_for_screen: assertion `GDK_IS_SCREEN (screen)' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: GtkWarning: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: GtkWarning: gdk_keymap_get_for_display: assertion `GDK_IS_DISPLAY (display)' failed
  self._scrollwin.add(self._textview)
/usr/lib/python2.5/site-packages/smart/interfaces/gtk/log.py:59: Warning: g_object_get: assertion `G_IS_OBJECT (object)' failed
  self._scrollwin.add(self._textview)
Segmentation fault (core dumped)
```

I installed Smart-PM via Adept, using default repositories.

---

### Post by Typhon on 2007-04-24
<bump>

---

### Post by Gustav on 2007-04-24
It seems to me as the gui is in gtk.

Do you have gtk installed?

---

### Post by Typhon on 2007-04-24
Yes I have. I just noticed a curious thing: if I run it in normal user mode, GUI starts without any errors, but when I run it as a root user, the GUI doesn't show up.

---

### Post by Typhon on 2007-04-25
[SIZE="5"][COLOR="Red"]SOLUTION FOUND[/COLOR][/SIZE]

[LIST][*]To run Smart GUI through **Alt+F2 window**, you must type *kdesu "smart --gui"* (or *gksu* for gnome) - those quotation marks are important, so don't forget them. 
[*]To run Smart through **KMenu** --> Command field: *smart --gui* (withour quotation marks) --> check box Run as a different user: root
[*] I don't know about Gnome menu. Sorry.[/LIST]

---

