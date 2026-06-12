---
title: "Compiz themer won't work"
date: 2006-07-21
forum: General Help
---

### Post by Grog140 on 2006-07-21
I updated Compiz Themer today and then when I did that I lost the ability to apply the themes. There used to be an option that would auto update my boarders but now there is none!

So I am stuck with the default theme.

Is this just me? Or and I missing something obvious?

---

### Post by thepizzaking on 2006-07-21
That's because they've now replaced gnome-window-decorator with cgwd, so run cgwd instead and it should work.;)

---

### Post by panurge77 on 2006-07-21
cgwd works fine, but gcompizthemer givers me a segfault :/

---

### Post by QUASAR_FREAK on 2006-07-22
i read in the compiz forums that doesnt work with edgy yet

---

### Post by brt on 2006-07-22
when trying to run cgwd i get:

cgwd: Connection Error (No reply within specified time)
5790: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4628.
This is normally a bug in some application using the D-BUS library.
5790: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4592.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
Aborted

---

### Post by brt on 2006-07-22
ahhh, now it works, just did an update from compizthemer now it works :D

---

### Post by testube_babies on 2006-07-22
For anyone else who is still having problems:
[http://www.ubuntuforums.org/showthread.php?p=1283090#post1283090](http://www.ubuntuforums.org/showthread.php?p=1283090#post1283090)

---

