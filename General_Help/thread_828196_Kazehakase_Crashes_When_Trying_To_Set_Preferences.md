---
title: "Kazehakase Crashes When Trying To Set Preferences"
date: 2008-06-13
forum: General Help
---

### Post by Mark76 on 2008-06-13
kazehakase

(kazehakase:8032): Gtk-CRITICAL **: gtk_tree_store_get_value: assertion `VALID_ITER (iter, tree_store)' failed

(kazehakase:8032): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.16.3/gobject/gtype.c:3368: type id `0' is invalid

(kazehakase:8032): GLib-GObject-WARNING **: can't peek value table for type `<invalid>' which is not currently referenced
Segmentation fault

:confused:

---

### Post by FakeOutdoorsman on 2008-06-13
[Kazehakase 0.5.3]("http://kazehakase.sourceforge.jp/") has the following bug fix:
> Fix a crash when preference dialog is opened.(Hiroyuki IKEZOE)
Ubuntu is currently using the previous version: 0.5.2.  Three related bug reports have been filed (one is for Intreped):
[Bug #173375: kazehakase crashed with SIGSEGV in gtk_tree_model_get_valist()]("https://bugs.launchpad.net/ubuntu/+source/kazehakase/+bug/173375")
[Bug #228918: kazehakase crash when open setting menu]("https://bugs.launchpad.net/ubuntu/+source/kazehakase/+bug/228918")
[Bug #239447: Kazehakase preferences crash the program]("https://bugs.launchpad.net/ubuntu/+source/kazehakase/+bug/239447")

---

### Post by Mark76 on 2008-06-13
Well. Looks like there's a new bug in 0.5.4. And this one crashes the browser when you try to do the one thing web browsers are made for :lol:

 > kazehakase

(kazehakase:11755): Kazehakase-CRITICAL **: kz_tab_label_new: assertion `KZ_IS_EMBED(kzembed)' failed

(kazehakase:11755): Gtk-CRITICAL **: gtk_widget_show_all: assertion `GTK_IS_WIDGET (widget)' failed

(kazehakase:11755): Gtk-CRITICAL **: gtk_widget_show: assertion `GTK_IS_WIDGET (widget)' failed

(kazehakase:11755): Gtk-CRITICAL **: gtk_notebook_insert_page: assertion `GTK_IS_WIDGET (child)' failed

(kazehakase:11755): Kazehakase-CRITICAL **: kz_notebook_get_sibling_tab_label: assertion `KZ_IS_TAB_LABEL(label)' failed

---

### Post by Mark76 on 2008-06-13
Ditto for 0.5.3. In case you were wondering

---

