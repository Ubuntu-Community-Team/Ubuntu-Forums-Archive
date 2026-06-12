---
title: "Add/Remove Applications not working...."
date: 2006-11-24
forum: General Help
---

### Post by BliND123 on 2006-11-24
Ok, I just got Xubuntu 6.10 installed, now after settings up my wireless I was trying to install applications with the new Add/Remove Applications I saw in the menu.  Every time I select something and it says I need internet connection to get it, I click Install.  Then it does nothing, its just stuck there with the Install button pressed, so I am just here waiting.  I couldn't find similar problems on the forum...how do I fix this?

---

### Post by marcantonio on 2006-11-24
Run gnome-app-install from a terminal.  It might give you more of an idea as to what the problem is.

Marc

---

### Post by BliND123 on 2006-11-24
Ah, this is what the terminal shows me when I did that:

```

Introspect error: The name org.freedesktop.AppInstall was not provided by any .service files
no listening object (The name org.freedesktop.AppInstall was not provided by any .service files)

** (gnome-app-install:4647): WARNING **: return value of custom widget handler was not a GtkWidget
/usr/lib/python2.4/site-packages/AppInstall/AppInstall.py:1270: GtkWarning: gtk_tree_model_sort: assertion `tree_model_sort->default_sort_func != NULL' failed
item.applications.set_default_sort_func(None)

```
How do I fix this?
And at the bottom of all that, was my "@ubuntu:" thing supposed to show up again? or is that only after I close the program that opened?

---

### Post by BliND123 on 2006-11-24
Anyone?  I can't get Streamtuner (besides other applications...like gnash) and I don't really know how to do it manually.

---

### Post by marcantonio on 2006-11-28
I'm not sure about that error message.  Can you use synaptic?
```
$ sudo synaptic
```

---

