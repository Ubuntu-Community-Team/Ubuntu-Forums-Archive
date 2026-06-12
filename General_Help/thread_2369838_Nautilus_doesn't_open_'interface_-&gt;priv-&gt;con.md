---
title: "Nautilus doesn't open: 'interface_-&gt;priv-&gt;connections != NULL' failed"
date: 2017-08-27
forum: General Help
---

### Post by greendalehumanbeing on 2017-08-27
Nautilus doesn't open from the launcher bar. Clicking causes the waiting icon, but then stops, and nothing happens. When I open Nautilus from the terminal, this is what I get:

```
$ nautilus

(nautilus:17625): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:17625): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Could not register the application: Timeout was reached

(nautilus:17625): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:17625): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:17625): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

```

I am using Nautilus: GNOME nautilus 3.14.3

and Ubuntu: 16.04 LTS

---

### Post by mc4man on 2017-08-27
Maybe try this for starters - 
right click on the nautilus icon in launcher > Unlock from Launcher

Then go Alt+F2
In the command box type this, press enter
```
gtk-launch nautilus
```

If nautilus opens ok an icon will show up in the launcher, r. click on it > Lock to Launcher
Then see if new icon works any better

---

### Post by greendalehumanbeing on 2017-08-27
Hi mc4man, thanks for the response. I'll try this the next time Nautilus fails and let you know what happens.

---

### Post by mc4man on 2017-08-28
> **greendalehumanbeing said:**
> Hi mc4man, thanks for the response. I'll try this the next time Nautilus fails and let you know what happens.
You didn't mention this was an intermittent issue.
In that case it's some bug nautilus has had recently. Simply just go Alt+F2 and enter
nautilus -q
Then click on icon to start up again.

If that doesn't work then use something like system-monitor to kill nautilus process

---

### Post by greendalehumanbeing on 2017-09-18
Thanks for your suggestion. Killing nautilus through terminal didn't work: ```
$ nautilus -q

(nautilus:2678): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed

(nautilus:2678): GLib-GIO-CRITICAL **: g_dbus_interface_skeleton_unexport: assertion 'interface_->priv->connections != NULL' failed
Could not register the application: Timeout was reached

(nautilus:2678): Gtk-CRITICAL **: gtk_icon_theme_get_for_screen: assertion 'GDK_IS_SCREEN (screen)' failed

(nautilus:2678): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(nautilus:2678): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion 'G_TYPE_CHECK_INSTANCE (instance)' failed

```

But killing the process through system-monitor worked and it re-started successfully. Any thoughts on why it keeps happening?

---

