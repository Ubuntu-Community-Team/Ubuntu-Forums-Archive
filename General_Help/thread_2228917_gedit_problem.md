---
title: "gedit problem"
date: 2014-06-10
forum: General Help
---

### Post by jgw on 2014-06-10
everytime I run gedit I get: (gedit:3548): Gtk-WARNING **: Calling Inhibit failed: GDBus.Error:org.freedesktop.DBus.Error.ServiceUnknown: The name org.gnome.SessionManager was not provided by any .service files

Thank you - Thoughts?

---

### Post by Impavidus on 2014-06-10
Does it work? I mean, when I run GUI applications from the command line, I get warnings like that all the time. Most of them don't seem to matter really.

---

### Post by bapoumba on 2014-06-10
Would you be using gedit as root with sudo ? If so, please use **gksudo gedit** instead.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by jgw on 2014-06-10
thank you for the replies

I would be using sudo with gedit.  I tried your suggestion and the error went away!

thank you!

---

### Post by bapoumba on 2014-06-10
Glad to got it to work :)
Please mark your thread as solved (under Thread tools), thanks.

---

