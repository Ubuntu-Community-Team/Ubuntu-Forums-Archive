---
title: "Trying to read ntbtlog.txt"
date: 2013-06-16
forum: General Help
---

### Post by anon_private on 2013-06-16
Hi,

I am trying to read the file ntbtlog.txt.

in GEdit it will not load properly, although what loads is readable (English).

The file loads in Libre Office Writer, but it is not readable (text, but characters, not English).

Can someone recommend a utility that will read this file (ca. 600 pages in length and about 3MB in size).

I am using Ubuntu 12.04.2 as a live pendrive.

Thanks

---

### Post by searchfgold6789 on 2013-06-16
Hi,
This is a UTF-16 encoded file, and (as far as I can tell from a quick Google) there is some sort of bug in Windows that does not set the encoding correctly. Open the file in UTF-16. This can be done with a terminal command... ```
gedit --encoding=UTF-16 ntbtlog.txt
``` or when the file is already opened in Gedit: [http://askubuntu.com/questions/98036/how-to-set-encoding-in-gedit-3-2](http://askubuntu.com/questions/98036/how-to-set-encoding-in-gedit-3-2)

---

### Post by anon_private on 2013-06-17
Thanks for reponding (I used: gedit --encoding=UTF-16 ntbtlog.txt)

I am getting this output:

(gedit:5712): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkSourceGutterRenderer'

(gedit:5712): GtkSourceView-CRITICAL **: gtk_source_gutter_renderer_get_view: assertion `GTK_SOURCE_IS_GUTTER_RENDERER (renderer)' failed

(gedit:5712): Gtk-CRITICAL **: gtk_text_view_get_buffer: assertion `GTK_IS_TEXT_VIEW (text_view)' failed

(gedit:5712): Gtk-CRITICAL **: gtk_text_buffer_get_line_count: assertion `GTK_IS_TEXT_BUFFER (buffer)' failed

(gedit:5712): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkSourceGutterRendererText'

(gedit:5712): GtkSourceView-CRITICAL **: gtk_source_gutter_renderer_text_measure_markup: assertion `GTK_SOURCE_IS_GUTTER_RENDERER_TEXT (renderer)' failed

(gedit:5712): GLib-GObject-WARNING **: invalid uninstantiatable type `(null)' in cast to `GtkSourceGutterRenderer'

(gedit:5712): GtkSourceView-CRITICAL **: gtk_source_gutter_renderer_set_size: assertion `GTK_SOURCE_IS_GUTTER_RENDERER (renderer)' failed

Ps

Regarding the terminals I have Term, UXTerm, and XTerm. What are the differences?

Thanks

---

### Post by searchfgold6789 on 2013-06-18
You probably just want to use the regular Terminal (ctrl+alt+T). I don't know exactly why UXterm and Xterm are provided. Some programs require them because they are a very simple, standard terminal that many distros use. As a computer user, you shouldn't need to use them (or see them). Ubuntu ships with its own terminal, known as Terminal, that is designed specifically to go with Ubuntu and provide a nice terminal for users.
Ignoring the GTK errors, did gedit even open? If it didn't, _open gedit as normal and load the file like you tried to do before_ and follow the instructions in the [link]("http://askubuntu.com/questions/98036/how-to-set-encoding-in-gedit-3-2") I gave you to change the read encoding to UTF-16 instead of UTF-8.

---

### Post by anon_private on 2013-06-18
I did use the code that you provided. The file will not open properly, and despite the command it tries to open as UTF-8

---

### Post by searchfgold6789 on 2013-06-22
Hi,
You will probably have better luck if you log in to Windows and try to read the file from there instead. Though it sounds like you are unable to do so. (Perhaps we can help you with the bigger problem you are having?)

---

