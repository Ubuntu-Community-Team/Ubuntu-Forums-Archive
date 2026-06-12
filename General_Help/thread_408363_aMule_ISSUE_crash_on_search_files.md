---
title: "aMule ISSUE: crash on search files"
date: 2007-04-13
forum: General Help
---

### Post by geco on 2007-04-13
Hello, I installed aMule from ubuntu repositories and I have this strange issue:
when I close the search windows in the search tab, aMule ceashes.

I am on Kubuntu 6.10 with KDE 3.5.6.

Here is the log:

```

(amule:6288): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(amule:6288): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

(amule:6288): Gtk-CRITICAL **: gtk_container_remove: assertion `GTK_IS_TOOLBAR (container) || widget->parent == GTK_WIDGET (container)' failed

Gtk-ERROR **: file gtkcontainer.c: line 2447 (gtk_container_propagate_expose): assertion failed: (child->parent == GTK_WIDGET (container))
aborting...
Aborted

```

Any comments or suggestions will be appreciated.

byebye

---

