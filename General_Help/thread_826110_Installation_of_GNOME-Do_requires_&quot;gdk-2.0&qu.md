---
title: "Installation of GNOME-Do requires &quot;gdk-2.0&quot;"
date: 2008-06-11
forum: General Help
---

### Post by spiritfox on 2008-06-11
I was attempting to install Gnome-Do from the source tarball available on its launchpad site, and got the following error when running ./configure:

```
checking for LIBDO... configure: error: Package requirements (glib-2.0 gdk-2.0 gdk-x11-2.0 gtk+-2.0) were not met:

No package 'gdk-2.0' found
No package 'gdk-x11-2.0' found
No package 'gtk+-2.0' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBDO_CFLAGS
and LIBDO_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

```
Where might I get these packages?

---

### Post by prince_niceguy on 2008-06-11
gnome do is in the repos of hardy too you can use that.

---

### Post by spiritfox on 2008-06-11
I was actually specifically looking to install version 0.5, which isn't in the repos yet.

---

### Post by priegog on 2008-06-12
But on the gnome-do page, they redirect you to a page that contains a repo that you can add that has 0.5

---

### Post by spiritfox on 2008-06-12
Oh!  I hadn't seen that!  thanks a lot!

---

### Post by priegog on 2008-06-12
mind you that at least for me (and I'm waiting for confirmation from other people on another thread) that version when installed on hardy SEEMS to work, but when you select an action and hit enter, nothing happens. Try it out and please let me know if it works for you or not so I can have more evidence to issue a bug report.

---

### Post by topgi on 2008-06-13
Same issue for me. After installation I cannot use any plugins. It works only partially.

---

### Post by priegog on 2008-06-13
Ah, thanks. I'm off to look if a bug report has already been submitted.

---

