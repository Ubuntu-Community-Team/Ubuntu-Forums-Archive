---
title: "Can't open Software Sources (among others)"
date: 2012-11-28
forum: General Help
---

### Post by seanos on 2012-11-28
My media PC running Natty seems to have developed some mysterious problems.  First it was giving me a notification about update failures - it hadn't done an update check in 13 days.  Running a check with Update Manager failed.  Running from terminal showed that the problem line was...

```
deb http://extras.ubuntu.com/ubuntu natty main #Third party developers repository
```However if I try to access Software Sources from the Software Center or settings in Update Manager, it fails *silently*.

In terminal...

```
sean@urania:~$ gksu /usr/bin/software-properties-gtk
g_dbus_connection_real_closed: Remote peer vanished with error: Underlying GIOStream returned 0 bytes on an async read (g-io-error-quark, 0). Exiting.
```Thought I could run root gedit (menu command: gksu gedit %U) to fix it manually, but that also fails.  Used to work, but now I only get the Starting Administration Application prompt.  From a terminal I get this...

```
GLib-GIO:ERROR:/build/buildd/glib2.0-2.28.6/./gio/gdbusconnection.c:2279:initable_init: assertion failed: (connection->initialization_error == NULL)
```I seem to get a similar dbus error for other gksu command that used to work; some just fail silently (e.g. gksu nautilus).

I've since used nano to comment out the extras repo (why should this be failing anyway?) and successfully done an update check (there weren't any) but would like to know why these other programs are failing.

In other weirdness, a post-processor (augment_timezone) for Shepherd (tv guide data grabber) failed meaning my tv guide is out by 12 hours.

Currently running a disk check, but SMART reports the disks are fine.

---

### Post by claracc on 2012-11-29
Ubuntu natty 11.04 reached its end of life on october 28, 2012. [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases), so you will not receive any more updates.

You will have to move to a supported ubuntu release

---

### Post by seanos on 2012-11-29
That's all well and good, but doesn't explain why these things aren't working.

---

