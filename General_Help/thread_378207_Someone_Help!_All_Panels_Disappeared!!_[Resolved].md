---
title: "Someone Help! All Panels Disappeared!! [Resolved]"
date: 2007-03-07
forum: General Help
---

### Post by acwspoon on 2007-03-07
My panels disappeared after I was messing around with desklets and now when i log-on my panels are gone.... when i try

```
gnome-panel
```

it says

```
(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(gnome-panel:9051): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

```

and then a window pops up and says I've already detected a panel running....

I'm clueless on what to do....

Please Help!
Thanks

---

### Post by ZERO_SHIFT on 2007-03-07
Hi,

You could try loging in the safe session mode (Login Menu) and then you may try to disable Desklets from there.


Good luck

---

### Post by aysiu on 2007-03-07
Not sure if this'll fix your issue, but you may want to check [this fix](http://www.macewan.org/2006/11/19/gtk-warning-unable-to-locate-theme-engine-in-module_path-pixmap/) out.

---

### Post by acwspoon on 2007-03-07
I fixed it!.... I recently added sidecandy cpu, ram, and network desklets but already had desklets as a start up application but i just got rid of all the sidecandy desklets and restarted and everything was fine... I'm really not sure what happened or why they prevented gnome from working but everything is back to normal... thanks for the help though

---

