---
title: "Realplayer Real Problem!!!!!!!!!"
date: 2005-05-22
forum: General Help
---

### Post by hammett111 on 2005-05-22
When I start RealPlayer 10 it doesn't open. When I run it in the terminal this is the out put. ANyone gimme a clue as to whats going on??

root@ubuntu:/opt/RealPlayer # realplay

(realplay.bin:8697): Gdk-WARNING **: locale not supported by Xlib

(realplay.bin:8697): Gdk-WARNING **: can not set locale modifiers

(realplay.bin:8697): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:8697): Gdk-WARNING **: Error converting from UTF-8 to STRING: Conversion from character set 'UTF-8' to 'ISO-8859-1' is not supported

(realplay.bin:8697): Gtk-WARNING **: /usr/lib/gtk-2.0/2.4.0/engines/libthinice.so: cannot open shared object file: No such file or directory
Failed to load pixbuf file: /opt/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

(realplay.bin:8697): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8697): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8697): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8697): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8697): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed

(realplay.bin:8697): GdkPixbuf-CRITICAL **: file gdk-pixbuf-io.c: line 770 (gdk_pixbuf_new_from_file): assertion `error == NULL || *error == NULL' failed
Failed to load pixbuf file: /opt/RealPlayer/share/realplay/icon.png: Unable to load image-loading module: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.4.0/loaders/libpixbufloader-png.so: cannot open shared object file: No such file or directory

** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
** (realplay.bin:8697): WARNING **: /usr/lib/pango/1.4.0/modules/pango-basic-fc.so: cannot open shared object file: No such file or directory
Failed to load Pango module for id: 'BasicScriptEngineFc'
(realplay.bin:8697): GLib-GObject-CRITICAL **: file gobject.c: line 1561 (g_object_ref): assertion `G_IS_OBJECT (object)' failed

** (realplay.bin:8697): CRITICAL **: file pango-engine.c: line 68 (_pango_engine_shape_shape): assertion `PANGO_IS_FONT (font)' failed

** ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
aborting...
/usr/bin/realplay: line 75:  8697 Aborted                 $REALPLAYBIN "$@"

---

### Post by derrick1985 on 2005-05-22
try

killall esd

then run realplay

---

### Post by hammett111 on 2005-05-23
No luck with killall esd, or setting default sound to ALSA.....

---

### Post by gabbman on 2005-05-23
[QUOTE=derrick1985]try

killall esd

then run realplay[/QUOTE]

That fixed it.

---

