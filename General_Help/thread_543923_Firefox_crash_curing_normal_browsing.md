---
title: "Firefox crash curing normal browsing"
date: 2007-09-05
forum: General Help
---

### Post by voided3 on 2007-09-05
I've been getting some random crashes on FF and Epiphany when browsing around. Here's the terminal output on the 'fox:



> (Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed

(Gecko:13934): Gtk-CRITICAL **: gtk_widget_set_size_request: assertion `height >= -1' failed
Segmentation fault (core dumped)




I assume the Gtk widget it is referring to are something to do with video plugins, but do you guys have any ideas? Thanks!

---

### Post by voided3 on 2007-09-10
Alrighty, I think I got it figured out. Since the same computer does it in windows as well, I experimented with various hardware changes and found that it was a stick of a ram, so unfortunately now i'm down from 2 GB to 1.5 GB, but that still is ample for Ubuntu and XP so no big loss. If it happens do that in the future again though, i'll be back and asking questions.

---

