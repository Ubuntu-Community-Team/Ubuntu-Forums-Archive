---
title: "Cant access Login window from System-&gt;Administration"
date: 2008-06-05
forum: General Help
---

### Post by Berto88 on 2008-06-05
Hi,

Im trying to install a new GDM theme, but when i go system -> administration, a window opens on the bottom bar saying "starting login window" but then nothing happens.

---

### Post by Forlong on 2008-06-05
Run ```
sudo gdmsetup
``` in a terminal.

If it spits out a segfault -- that seems to be a bug, that has already been mentioned here in another thread.
Consider filing a bugreport then.


edit: it works here without a problem, btw.

---

### Post by Berto88 on 2008-06-05
yup a segmentation fault popped out, how do i file a bug report?

---

### Post by Forlong on 2008-06-05
Running this in the terminal should be of major help:
```
apport-cli -f -p gdm
```

---

### Post by billstei on 2008-06-08
I am seeing the same thing with the Starting Login going away and then after several minutes the Login window appears.  No seg fault from the terminal with sudo gdmsetup.

Bill

---

### Post by aeg1s on 2008-09-07
The exact same thing is happening to me... Login Window starts, disappears, and a taskbar window that says "Starting..." disappears a few seconds later.

---

### Post by laloruelas on 2008-09-14
would reinstalling the system fix anything

---

### Post by csaga on 2008-10-15
It's happened exactly the same things. The solution is only to reinstall the system?
Thanks for help!

---

### Post by bmw4l1f3 on 2008-10-31
so its been two weeks and this problem still hasn't been resolved.  I remember being able to do it when I initially changed my theme/login.  But as of the last couple of days I can't get into it.  How do I file a bug report?

---

### Post by csaga on 2008-11-03
When I try running in Terminal gksudo gdmsetup get the fallowed error:

gdmsetup[6901]: GLib-CRITICAL: g_error_free: assertion `error != NULL' failed
gdmsetup[6901]: GLib-GIO-CRITICAL: g_simple_async_result_set_from_error: assertion `error != NULL' failed
gdmsetup[6901]: GLib-GIO-WARNING: (/build/buildd/glib2.0-2.16.6/gio/gfile.c:5249):IA__g_file_load_partial_contents_finish: runtime check failed: (g_simple_async_result_get_source_tag (simple) == g_file_load_contents_async)

---

### Post by bmw4l1f3 on 2008-11-04
So I got this to work finally.  and how you ask?


I installed Ubuntu 8.10....  I tried the upgrade, had some issues, didn't want to mess with it, had allready backed up my files so I installed it over my existing distro...

---

