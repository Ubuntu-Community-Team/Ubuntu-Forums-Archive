---
title: "Wireshark no longer works"
date: 2014-07-12
forum: General Help
---

### Post by DigiAngel on 2014-07-12
I can start it...but as soon as I try and open a file it locks up.  Running in terminal I get:

(wireshark:3247): Gtk-CRITICAL **: gtk_orientable_get_orientation: assertion 'GTK_IS_ORIENTABLE (orientable)' failed
(wireshark:3247): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GtkScrollbar'
(wireshark:3247): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GtkWidget'
(wireshark:3247): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GObject'
(wireshark:3247): GLib-GObject-CRITICAL **: g_object_get_qdata: assertion 'G_IS_OBJECT (object)' failed
(wireshark:3247): Gtk-CRITICAL **: gtk_widget_set_name: assertion 'GTK_IS_WIDGET (widget)' failed
(wireshark:3247): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GObject'
(wireshark:3247): GLib-GObject-CRITICAL **: g_object_set_qdata_full: assertion 'G_IS_OBJECT (object)' failed
(wireshark:3247): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GtkRange'
(wireshark:3247): Gtk-CRITICAL **: gtk_range_get_adjustment: assertion 'GTK_IS_RANGE (range)' failed
(wireshark:3247): GLib-GObject-WARNING **: invalid unclassed pointer in cast to 'GtkOrientable'

Anyone else seeing this?  Thank you.

---

### Post by ubudog on 2014-07-12
Hi,

From [this]("https://bugs.launchpad.net/ubuntu/+source/wireshark/+bug/1208583") bug report, can you try:
```
export LIBOVERLAY_SCROLLBAR=0
wireshark
```

Does that fix the problem?

---

### Post by DigiAngel on 2014-07-12
I'll be darned....yea that sure was...thank you so much for the intel on that!

---

### Post by ubudog on 2014-07-12
Glad it works!  Which Ubuntu release are you using?

---

### Post by chtodd on 2015-01-30
I experienced this problem under Trusty (14.04).  Thanks for the tip.  I added that to my bashrc.

---

