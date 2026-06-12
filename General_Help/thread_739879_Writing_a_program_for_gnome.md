---
title: "Writing a program for gnome?"
date: 2008-03-30
forum: General Help
---

### Post by bigblop on 2008-03-30
How do I get started writing an app for gnome? Would like to write a virtual desktop manager.

---

### Post by conscious on 2008-03-30
If you're planning a graphical application, you should use GTK+:
[http://www.gtk.org/](http://www.gtk.org/)

---

### Post by prismpirate on 2008-03-30
Doesn't gnome already come with virtual desktops? At least it does in ubuntu

---

### Post by bigblop on 2008-03-30
No it only supports a tiny one in the panel. I would like to write an larger one that can be moved around freely.

---

### Post by Nameless_one on 2008-03-30
You might also want to check [the gnome development site](http://www.psychocats.net/ubuntu/index.php).

---

### Post by bigblop on 2008-03-30
> **conscious said:**
> If you're planning a graphical application, you should use GTK+:
[http://www.gtk.org/](http://www.gtk.org/)

Hm on the website it says that I need:

    * GTK+ 2.12
    * GLib 2.14
    * Pango 1.18


But I cannot find any of these packages. Do I need to build them all from scratch?

EDIT: Why not use Qt instead of GTK+?

---

### Post by Nameless_one on 2008-03-30
The packages you need are 

libgtk2.0-dev libglib2.0-dev libpango1.0-dev

In Gutsy, they are the correct versions. Of course, you can build from scratch if you want newer versions.

---

### Post by conscious on 2008-03-30
> **bigblop said:**
> Why not use Qt instead of GTK+?

Sure, you can use Qt, but it's native for KDE just like GTK+ is for GNOME.

---

### Post by bigblop on 2008-03-30
> **conscious said:**
> Sure, you can use Qt, but it's native for KDE just like GTK+ is for GNOME.

Thanks. I found something called gtkmm which should be a C++ wrapper for GTK+. Should I go for GTK+ or gtkmm when writing a virtual desktop manager?

---

### Post by Nameless_one on 2008-03-30
The real choice is what programming language you will use, I believe. GTK+ is C, if you prefer C++ you will need gtkmm. 

I haven't writeen any applications for gnome though, I don't know if  gtkmm has any performance difference than using pure GTK+.

---

