---
title: "Linux DC++ client issues"
date: 2006-11-14
forum: General Help
---

### Post by mindshift on 2006-11-14
Hey everyone, i was wondering if you could help me troubleshoot an issue im having with edgy and Linux Dc++. I followed the directions on this thread 
[http://www.ubuntuforums.org/showthread.php?t=28378](http://www.ubuntuforums.org/showthread.php?t=28378) and replaced all the outdated packages with newer ones. Then followed the rest of the directions until i was able to run it from the linuxdcpp folder. So now i want to have it handy and add it to my menu. So, i open menu editor, browse for and select my executable, and then try and run it from the menu and nothing happens. So next i try to run it with the console and i get the following message:

```
alex@alex-desktop:~$ '/home/alex/linuxdcpp/linuxdcpp'
Loading: Hash database
Loading: Shared Files
Loading: Download Queue
/usr/local/share/linuxdcpp is inaccessible, falling back to current directory instead.

(linuxdcpp:6399): libglade-WARNING **: could not find glade file './glade/mainwindow.glade'

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_main_quit: assertion `main_loops != NULL' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_dialog_set_alternative_button_order: assertion `GTK_IS_DIALOG (dialog)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_dialog_set_alternative_button_order: assertion `GTK_IS_DIALOG (dialog)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_dialog_set_alternative_button_order: assertion `GTK_IS_DIALOG (dialog)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tool_button_set_icon_widget: assertion `GTK_IS_TOOL_BUTTON (button)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_about_dialog_set_logo: assertion `GTK_IS_ABOUT_DIALOG (about)' failed

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

(linuxdcpp:6399): Gtk-WARNING **: Error loading icon from file './pixmaps/linuxdcpp-icon.png':
        Failed to open file './pixmaps/linuxdcpp-icon.png': No such file or directory

(linuxdcpp:6399): Gtk-WARNING **: Error loading icon from file './pixmaps/linuxdcpp-icon.png':
        Failed to open file './pixmaps/linuxdcpp-icon.png': No such file or directory

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_widget_set_sensitive: assertion `GTK_IS_WIDGET (widget)' failed

(linuxdcpp:6399): libglade-CRITICAL **: glade_xml_get_widget: assertion `self != NULL' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_set_headers_clickable: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(linuxdcpp:6399): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_insert_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_set_model: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_get_selection: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_selection_set_mode: assertion `GTK_IS_TREE_SELECTION (selection)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_column_set_sort_column_id: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_column_set_sort_column_id: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_column_set_sort_column_id: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed

(linuxdcpp:6399): GLib-GObject-WARNING **: invalid unclassed pointer in cast to `GtkTreeSortable'

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_sortable_set_sort_column_id: assertion `GTK_IS_TREE_SORTABLE (sortable)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_get_column: assertion `GTK_IS_TREE_VIEW (tree_view)' failed

(linuxdcpp:6399): Gtk-CRITICAL **: gtk_tree_view_column_set_sort_indicator: assertion `GTK_IS_TREE_VIEW_COLUMN (tree_column)' failed
Segmentation fault (core dumped)
```

is there any way i can fix this so i can run linux DC++ from my menu




also on a side note: i need to use a port knocker to get on my hub of choice, could anyone reccomend a program that would work well with ubuntu? thanks.

---

### Post by tzepu on 2008-02-26
hello al , i am a linux newbie( this is my first time:)))) and i got another problem with my linuxdc++, after few seconds i started it i get this error
** ERROR **: file gailtreeview.c: line 3724 (traverse_cells): assertion failed: (row_path != NULL)
aborting...
Aborted (core dumped)
@mindshift try this to restart your dc++ client (it did not worked for me though) 
 rm -r ~/.dc++
thanks in advance

---

