---
title: "Apearences freezes"
date: 2007-10-20
forum: General Help
---

### Post by matthew.lns1 on 2007-10-20
The appeareces diolog freezes when ever I try to use it. I ran it in terminal and got some interesting error messages:
```

Gtk-Message: Failed to load module "gnomeb
open shared object file: No such file or d
Gtk-Message: Failed to load module "gnomeb
open shared object file: No such file or d
/home/matthew/.themes/leopard/gtk-2.0/gtkr
pixmap_path: "Lines/line-v.png"
/home/matthew/.themes/leopard/gtk-2.0/gtkr
ied without filename
/home/matthew/.themes/leopard/gtk-2.0/gtkr
 pixmap_path: "Menu-Menubar/menubar.png"
/home/matthew/.themes/leopard/gtk-2.0/gtkr
fied without filename

(gnome-appearance-properties:8233): Gtk-CR
GTK_WIDGET_VISIBLE (widget)' failed
sh: kde-config: not found
sh: kde-config: not found

```

Does anyone have any idea how I can get gnomebreakpad.so or how I can get  gnome-appearance-properties to work?

---

### Post by Eudaimonia on 2007-10-21
I get the same errormessage when loading modules with synaptic.

Gtk-Message **: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 54, <> line 13.
Gtk-Message **: Failed to load module "gnomebreakpad": libgnomebreakpad.so: cannot open shared object file: No such file or directory at /usr/share/perl5/Debconf/FrontEnd/Gnome.pm line 60, <> line 13.

---

### Post by matthew.lns1 on 2007-10-28
Is there any remedy?

---

### Post by matthew.lns1 on 2007-11-27
I removed "gtk-qt-engine" and now it's working fine.

---

