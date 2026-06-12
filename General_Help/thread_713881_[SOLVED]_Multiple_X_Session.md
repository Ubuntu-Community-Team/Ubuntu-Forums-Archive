---
title: "[SOLVED] Multiple X Session ??"
date: 2008-03-03
forum: General Help
---

### Post by chadeldridge on 2008-03-03
I am running 3 monitors each with seperate X sessions.  Is it possible to set an application on Session 2 to always start on Session 1?  For example is it possible to click a link on monitor 2 or 3 that will open in the already running firefox session on monitor 1?

Thanks

---

### Post by kuja on 2008-03-03
I'm not sure about the firefox bit, but making an app start in a different screen (generally speaking) is pretty easy to do.  You'll need to know the $DISPLAY value of each screen (ie: echo $DISPLAY), then, when you want to start something in say, screen 2, it might look something like this: "firefox -display :0.1"

---

### Post by chadeldridge on 2008-03-03
Thank you for starting me off in the right direction.  Sadly though it seems as there is no -display switch for firefox (at least no documented one from their site).  If there is something like this I suppose I would just have to set firefox to be started from a script then so that the -display line gets passed to the browser on every start?

---

### Post by kuja on 2008-03-03
the -display switch *should* affect every graphical app, as such, it's generally not in an applications documentation, as it'd be kind of redundant.

And yeah, you can do it from a script ...... or crreate an icon for it, or whatever.

---

### Post by chadeldridge on 2008-03-03
Do you happen to know the correct syntax for the -display switch.  I think i have tried them all with no luck FF always starts on the screen you launch it from.

firefox -display:0.0
firefox -display:0.1
firefox -display :0.1
firefox -display ":0.1"
firefox -display ":0.0"

Sorry for constant questions ... just happy that someone actually answered a post from me.

---

### Post by bodhi.zazen on 2008-03-03
It does not always work the same with every application.

If the -d flag does not work, try setting the display manually :

```
DISPLAY=:0
firefox
```

Sometimes you need localhost :

DISPLAY=localhost:0

You can set an alias for each display if you like.

---

### Post by chadeldridge on 2008-03-03
The -d does seem to exist, but when i specify a display other than its current i get Error: cannot open display: 1 (or whatever the current screen number is).

---

### Post by dark_phantom on 2008-03-03
Specify your hostname on the display.  Just replace hostname with your real hostname.

DISPLAY=hostname:0.0
export DISPLAY

---

### Post by chadeldridge on 2008-03-03
firefox -d:0.1
_X11TransSocketINETConnect() can't get address for celdridge-desktop:6000: Name or service not known
Error: cannot open display: celdridge-desktop:0.1

---

### Post by kuja on 2008-03-03
The syntax I showed was correct, however, the display number very well may not have been. Like I said, you need to check the display numbers by opening a shell in each screen, and "echo $DISPLAY" ing.

---

### Post by chadeldridge on 2008-03-06
This is still a no-go for me.  The -d modifier always returns the same error, even with the correct session name, which i have checked and rechecked.  

I would really appreciate some more help on this if possible.

---

### Post by chadeldridge on 2008-03-06
So to add some more insight it seems that other apps using the -d or -display setting work fine, it is just firefox that will not work.

xterm -d :0.1 works fine as does others.  I am using FF3r3 if that is at all helpful.



[B]celdridge@celdridge-desktop:~$ firefox -display :0.1

(gecko:5120): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:5120): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(gecko:5120): GLib-GObject-CRITICAL **: g_signal_handlers_disconnect_matched: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(gecko:5120): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gecko:5120): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:5120): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:5120): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:5120): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:5120): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:5120): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:5120): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:2180: invalid unclassed object pointer for value type `GdkScreen'

(gecko:5120): Gdk-CRITICAL **: gdk_screen_get_display: assertion `GDK_IS_SCREEN (screen)' failed

(gecko:5120): GLib-GObject-CRITICAL **: g_object_get_data: assertion `G_IS_OBJECT (object)' failed

(gecko:5120): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.14.1/gobject/gsignal.c:2180: invalid unclassed object pointer for value type `GdkScreen'

(gecko:5120): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
[/B]

---

### Post by chadeldridge on 2008-03-06
OK ... well I finally got it fixed, so anyone else with this issue check it out  It's very simple in the end.  Just start firefox -P on the second monitor and create a profile for the seperate X session. That's it .. done.

Thanks

---

