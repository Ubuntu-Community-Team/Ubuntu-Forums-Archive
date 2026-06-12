---
title: "Firefox 1.5.0.7 likes to crash"
date: 2006-10-13
forum: General Help
---

### Post by Weedman on 2006-10-13
Hello, this is my first post here at the Ubuntu forums.

I would like to mention beforehand, that this behaviour from Firefox has NOT been isolated to just Ubuntu. This has happened on Gentoo Linux as well, with the exact same version.

I (as of 1.5.0.7) am having extreme problems with Firefox. A simple routine close-of-a-tab, and firefox crashes. This behaviour don't seem attributed directly to a tab issue, I closed a popup window and FF crashed.

This is a nice crash dump I got from the popup crash:
```

(Gecko:7072): Gdk-WARNING **: GdkWindow 0x32c78ea unexpectedly destroyed

(Gecko:7072): Gdk-CRITICAL **: gdk_window_set_user_data: assertion `window != NULL' failed

(Gecko:7072): Gdk-CRITICAL **: gdk_window_set_back_pixmap: assertion `GDK_IS_WINDOW (window)' failed

(Gecko:7072): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(Gecko:7072): GLib-GObject-CRITICAL **: g_object_set_data: assertion `G_IS_OBJECT (object)' failed

(Gecko:7072): Gdk-CRITICAL **: gdk_window_move_resize: assertion `GDK_IS_WINDOW (window)' failed

(Gecko:7072): Gdk-CRITICAL **: gdk_window_show_unraised: assertion `GDK_IS_WINDOW (window)' failed

(Gecko:7072): Gdk-CRITICAL **: gdk_window_resize: assertion `GDK_IS_WINDOW (window)' failed
The application 'Gecko' lost its connection to the display :0.0;
most likely the X server was shut down or you killed/destroyed
the application.

```

I'm wondering if there are problems with GTK+ (or glib etc), instead of FF.

This is because one of my other GTK+ apps, quodlibet, has been crashing a bit on me as well, and it didn't do that before at all.

Thoughts?

weed

---

### Post by timetunnel on 2006-10-13
No idea really, but maybe it's an extension you installed? FF 1.5.0.7 works without any problems on my ubuntu 6.06. Do you use the package from the ubuntu repository, or did you download it from the Firefox site?

---

### Post by Weedman on 2006-10-13
Nup, it's from Ubuntu's repositories all right.

What extensions do you have installed? All bar about 2 or 3 were installed when I had 1.5.0.6 installed, and they worked without an issue.

weed

---

