---
title: "Getting `Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/"
date: 2015-12-12
forum: General Help
---

### Post by bhmerchant on 2015-12-12
I am having some errors with gtk/glib like so:

```
    GLib-GIO-Message: Using the 'memory' GSettings backend.  Your settings will not be saved or shared with other applications.
    
    (python:3369): Gtk-WARNING **: GModule (/usr/lib/x86_64-linux-gnu/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)
    
    (python:3369): Gtk-WARNING **: Loading IM context type 'ibus' failed
```

What packages should I install/re-install in order to make sure things are in order again?

These errors aren't coming out of nowhere, as I was unsuccessfully trying to install `pygtk` in the morning, and may have touched some `gtk` stuff by mistake. I don't know what I should do to fix it though :(

---

### Post by bhmerchant on 2015-12-13
Some things that I have tried since then, without any success:

0) reinstalling libglibc, gtk2, gtk3 and their dependencies

1) reinstalling ubuntu-desktop and its dependencies

2) reinstalling ubuntu over my current installation (I thought this would finally do it, but no luck)

What else could be issues that I can look into addressing?

---

### Post by bhmerchant on 2015-12-13
Solved the issue: I had PyQt5 installed along side the native PyQt4 that comes with my Anaconda python distribution, causing terrible problems. Lesson: stick with PyQt4 if using Anaconda.

---

### Post by bonnevie on 2016-08-17
> **bhmerchant said:**
> Solved the issue: I had PyQt5 installed along side the native PyQt4 that comes with my Anaconda python distribution, causing terrible problems. Lesson: stick with PyQt4 if using Anaconda.

I seem to be getting similar errors, and this sounds like the right fix - but I cannot for the life of me track down the offending package. How did you uninstall PyQt5 in the correct manner?

---

