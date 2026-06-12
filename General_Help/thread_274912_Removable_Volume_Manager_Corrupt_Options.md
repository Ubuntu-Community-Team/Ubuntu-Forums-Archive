---
title: "Removable Volume Manager Corrupt Options"
date: 2006-10-10
forum: General Help
---

### Post by Old Pink on 2006-10-10
Hello,

When trying to set my "Removable Devices and Media" preferences, I get an error like the screenshot below, where instead of options I get [a GnomeFileEntry]

Here's the terminal output:
> 
matt@matt-desktop:~$ gnome-volume-properties

(gnome-volume-manager:18074): libglade-WARNING **: Could not load support for `gnome': libgnome.so: cannot open shared object file: No such file or directory

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): libglade-WARNING **: unknown widget class 'GnomeFileEntry'

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_entry_set_text: assertion `GTK_IS_ENTRY (entry)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid cast from `GtkLabel' to `GnomeFileEntry'

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_file_entry_gnome_entry: assertion `GNOME_IS_FILE_ENTRY (fentry)' failed

(gnome-volume-manager:18074): GnomeUI-CRITICAL **: gnome_entry_set_history_id: assertion `gentry != NULL' failed

(gnome-volume-manager:18074): Gtk-CRITICAL **: gtk_combo_set_case_sensitive: assertion `GTK_IS_COMBO (combo)' failed

(gnome-volume-manager:18074): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gnome-volume-manager:18074): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed
Any ideas at all? Please don't ignore this thread! :(

---

### Post by Old Pink on 2006-10-10
Now it works if I use ```
LD_PRELOAD="/usr/lib/libglade/2.0/libgnome.so" gnome-volume-properties
``` in terminal...

---

### Post by Mr Frosti on 2006-10-10
The Ubuntu community would never ignore your thread :)

As for the error you are receiving, it sounds like it could be an issue related to the theme you are using, or a corruption of the "gnome-volume-properties" being corrupted.

Try using a different theme in Gnome. If this doesn't resolve the issue, try reinstalling that package. This can be done using the code below:

```
sudo apt-get install gnome-volume-manager --reinstall
```

I am using version 2.15.0-0ubuntu6 without any issues.

---

### Post by Old Pink on 2006-10-10
Sorry, but you're wrong.

It's nothing to do with my theme, or the installation. It's because of my new version of libglade moving my libgnome.so file to /usr/lib/libglade/2.0/

So I have to open with[FONT=Verdana,Arial,Sans-Serif] [/FONT]```
LD_PRELOAD="/usr/lib/libglade/2.0/libgnome.so" gnome-volume-properties
``` which shows the application where the file is.

If I could copy the file to the original location, all would be solved, but I don't know exactly where the original location is...

---

### Post by srt4play on 2006-10-11
> **Matt.H said:**
> Sorry, but you're wrong.


His was actually a good suggestion, I've had themes disrupt the operation of certain programs before. 

I'd have a little bit kinder words than you for someone who was trying to help.

---

