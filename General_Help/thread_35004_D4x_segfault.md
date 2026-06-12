---
title: "D4x segfault"
date: 2005-05-17
forum: General Help
---

### Post by Dax0r on 2005-05-17
Why when I run the download manager d4x I get segmentation fault?
I tried also to compile from source but I get the same error.

---

### Post by harryc on 2005-05-17
Run d4x as user in a console. Post the output here.

---

### Post by ow50 on 2005-05-17
D4X segfaults if you use themes Glider or SmoothGNOME.

---

### Post by Dax0r on 2005-05-17
[QUOTE=harryc]Run d4x as user in a console. Post the output here.[/QUOTE]

When I run in a console I get "Segmentation Fault" ,this is the output :) 

> D4X segfaults if you use themes Glider or SmoothGNOME. 

I use Amaranth theme with Edge icons

---

### Post by bored2k on 2005-05-17
Any of you ever tried gwget + fireget extension[firefox] ? It's nice and light..

---

### Post by ow50 on 2005-05-17
[QUOTE=Dax0r]I use Amaranth theme with Edge icons[/QUOTE]
Does d4x segfault with Clearlooks?

About the gwget: You can get the latest hoary package at
[http://www.gnome.org/~davidsf/ubuntu/hoary/](http://www.gnome.org/~davidsf/ubuntu/hoary/)

---

### Post by Dax0r on 2005-05-18
I installed Gwget from source but I have another problem,it dont work properly... :-? 
When I run gwget in a console I get this:

> (gwget:21014): libglade-WARNING **: could not find `gnome' init function: `glade _module_register_widgets': /usr/lib/libgnome.so: undefined symbol: glade_module_ register_widgets

(gwget:21014): libglade-WARNING **: Could not load support for `bonobo': libbono bo.so: cannot open shared object file: No such file or directory

(gwget:21014): libglade-WARNING **: unknown widget class 'GnomeApp'

(gwget:21014): libglade-WARNING **: could not find `gnome' init function: `glade _module_register_widgets': /usr/lib/libgnome.so: undefined symbol: glade_module_ register_widgets

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_set_model: assertion `GTK_IS_TREE_ VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_selection_set_mode: assertion `GTK_IS_T REE_SELECTION (selection)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_append_column: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_selection_select_iter: assertion `GTK_I S_TREE_SELECTION (selection)' failed

(gwget:21014): libglade-WARNING **: could not find `gnome' init function: `glade _module_register_widgets': /usr/lib/libgnome.so: undefined symbol: glade_module_ register_widgets

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE _VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_column_set_visible: assertion `GTK _IS_TREE_VIEW_COLUMN (tree_column)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_resize: assertion `GTK_IS_WINDOW (win dow)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_move: assertion `GTK_IS_WINDOW (windo w)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_toolbar_set_style: assertion `GTK_IS_TOOLBAR  (toolbar)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_I S_CHECK_MENU_ITEM (check_menu_item)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_check_menu_item_get_active: assertion `GTK_I S_CHECK_MENU_ITEM (check_menu_item)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widge t)' failed
** Message: Cant create corba factory

** (gwget:21014): CRITICAL **: gwget_handle_automation_cmdline: assertion `serve r != NULL' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_ IS_TREE_SELECTION (selection)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_ IS_TREE_SELECTION (selection)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_T REE_VIEW (tree_view)' failed

(gwget:21014): Gtk-CRITICAL **: gtk_tree_selection_get_selected: assertion `GTK_ IS_TREE_SELECTION (selection)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_present: assertion `GTK_IS_WINDOW (wi ndow)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_present: assertion `GTK_IS_WINDOW (wi ndow)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_present: assertion `GTK_IS_WINDOW (wi ndow)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_present: assertion `GTK_IS_WINDOW (wi ndow)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed

(gwget:21014): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GtkWind ow'

(gwget:21014): Gtk-CRITICAL **: gtk_window_present: assertion `GTK_IS_WINDOW (wi ndow)' failed
** Message: docket clicked

(gwget:21014): Gdk-CRITICAL **: gdk_window_get_state: assertion `GDK_IS_WINDOW ( window)' failed

---

### Post by ow50 on 2005-05-18
[QUOTE=Dax0r]I installed Gwget from source but I have another problem,it dont work properly... :-? 
When I run gwget in a console I get this:[/QUOTE]
I can't tell what the problem is, but do you really need to install from source? Use the link I posted above for a deb of version 0.94. The lastest version is 0.95 so it's not that old.

---

