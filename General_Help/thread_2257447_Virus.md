---
title: "Virus?"
date: 2014-12-19
forum: General Help
---

### Post by petermartin2 on 2014-12-19
I keep getting this in terminal:

```
(gedit:11560): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files
```


what does it mean? Is it a virus?

---

### Post by grahammechanical on 2014-12-19
It is not a virus. What command are you running? What utility are you loading through the terminal? Is it Gedit? When we launch GUI applications from the terminal and not from their launcher icons we are liable to get various GtK-WARNING messages. GtK is the tool kit used to create the Graphical User Interface (GUI).

[http://www.gtk.org/](http://www.gtk.org/)

Regards.

---

### Post by petermartin2 on 2014-12-19
I see. Yes it was gedit - thanks a bunch!

---

