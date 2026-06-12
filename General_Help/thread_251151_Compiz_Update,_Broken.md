---
title: "Compiz Update, Broken?"
date: 2006-09-05
forum: General Help
---

### Post by ~LoKe on 2006-09-05
Well, a little while ago I updated Compiz and that whole bit, then after restarting my machine, I've lost my window borders.  So, I try to run startcompiz from the terminal, I get this error:

> compiz: Couldn't load plugin 'gconf'

This can't be good.  Any suggestions?

**EDIT:** Running it with sudo provides a little more error information:

> loke@x04d:~$ sudo startcompiz
loke@x04d:~$ cgwd: Connection Error (No reply within specified time)
5382: arguments to dbus_connection_get_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4629.
This is normally a bug in some application using the D-BUS library.
5382: arguments to dbus_connection_set_data() were incorrect, assertion "connection != NULL" failed in file dbus-connection.c line 4593.
This is normally a bug in some application using the D-BUS library.

** ERROR **: Not enough memory to set up DBusConnection for use with GLib
aborting...
compiz: Couldn't load plugin 'gconf'


---

### Post by frup on 2006-09-05
i have lost my window borders too

---

### Post by ~LoKe on 2006-09-05
Problem, er, resolved.  Looks like gconf isn't used anymore.  start-compiz is the script to execute now.

---

### Post by grte on 2006-09-05
More specifically, /usr/bin/compiz-start

Update your startup programs (or however you do it) accordingly.

Also, to edit your compiz settings, you'll now want to use the program "csm," rather than gconf-editor.

---

### Post by ~LoKe on 2006-09-05
That was...interesting.  Out of nowhere it stopped working again, so I ran compiz-start from the terminal.  Still nothing.  I added it to my start up list, still nothing.

Any ideas?

---

### Post by grte on 2006-09-05
> **~LoKe said:**
> That was...interesting.  Out of nowhere it stopped working again, so I ran compiz-start from the terminal.  Still nothing.  I added it to my start up list, still nothing.

Any ideas?

Try restarting gdm

```
sudo /etc/init.d/gdm restart
```

---

### Post by ~LoKe on 2006-09-05
That seems to have fixed it.  The more pressing matter is...why does compiz crash when I hit maximize? =D

---

### Post by grte on 2006-09-05
> **~LoKe said:**
> That seems to have fixed it.  The more pressing matter is...why does compiz crash when I hit maximize? =D

I haven't got an answer for that one.  I'd check out the compiz forums at compiz.org.

---

### Post by Dinerty on 2006-09-05
head over to:

[http://www.ubuntuforums.org/showthread.php?t=250489](http://www.ubuntuforums.org/showthread.php?t=250489)

alot of info there on the current updates :)

---

