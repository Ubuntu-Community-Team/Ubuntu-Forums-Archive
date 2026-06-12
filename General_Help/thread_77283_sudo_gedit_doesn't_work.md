---
title: "sudo gedit doesn't work"
date: 2005-10-16
forum: General Help
---

### Post by nszabolcs on 2005-10-16
i have a fresh breezy install.
```

gedit

```
works

but
```

sudo gedit

```
doesn't open the gedit window and i have to Ctrl+C to get back the shell prompt.

any ideas?

---

### Post by solar on 2005-10-16
[QUOTE=nszabolcs]i have a fresh breezy install.
```

gedit

```
works

but
```

sudo gedit

```
doesn't open the gedit window and i have to Ctrl+C to get back the shell prompt.

any ideas?[/QUOTE]

I have a simlar problem just when i am using network.
It seems that all the Gnome application that lauched by sudo are freezed, but if you waite about a few minutes, then the application will come out.

---

### Post by nszabolcs on 2005-10-16
LOL
```

nsz@ubuntu:~$ time sudo gedit

** (gedit:7927): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:7927): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:7927): CRITICAL **: gedit_prefs_manager_get_bool: assertion `gedit_prefs_manager->gconf_client != NULL' failed

** (gedit:7927): CRITICAL **: gedit_prefs_manager_get_int: assertion `gedit_prefs_manager->gconf_client != NULL' failed

(gedit:7927): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `GObject'

(gedit:7927): GLib-GObject-WARNING **: instance of invalid non-instantiatable type `<invalid>'

(gedit:7927): GLib-GObject-CRITICAL **: g_signal_connect_object: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gedit:7927): GLib-GObject-WARNING **: invalid uninstantiatable type `<invalid>' in cast to `BonoboMDI'

** (gedit:7927): CRITICAL **: bonobo_mdi_add_child: assertion `BONOBO_IS_MDI (mdi)' failed

** (gedit:7927): CRITICAL **: gedit_file_new: assertion `ret != FALSE' failed

real    3m9.576s
user    0m0.372s
sys     0m0.032s

```

3min and still no window :(

well, at least nautilus started after 3min...

this is really annoying especially because the unofficial ubuntuguide.org always uses "sudo gedit" for text file editing

 and the tips&tricks HOWTO-s use "sudo gedit" a lot as well

---

### Post by flipkick on 2005-10-17
Get the same "error". As well as with the logout function.
Have to use "Strg + Alt + Backspace" to logout.


Edit:

type "passwd" into the console.

then change your passwd. Now it should work fine again.

---

### Post by brentoboy on 2005-10-17
try:
gksudo gedit

sudo all by itself doenst know how to ask for a password in a gui environment.

happy sailing.

---

