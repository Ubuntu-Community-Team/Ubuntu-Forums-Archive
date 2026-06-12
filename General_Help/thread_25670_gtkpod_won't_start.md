---
title: "gtkpod won't start"
date: 2005-04-10
forum: General Help
---

### Post by Joh_ on 2005-04-10
I'm trying to start gtkpod to be able to transer music to my ipod. This is what i get:
```
(gtkpod:12569): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gtkpod:12569): Pango-CRITICAL **: _pango_engine_shape_covers: assertion `PANGO_IS_FONT (font)' failed

(gtkpod:12569): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed

(gtkpod:12569): Pango-CRITICAL **: _pango_engine_shape_shape: assertion `PANGO_IS_FONT (font)' failed

Pango-ERROR **: file shape.c: line 75 (pango_shape): assertion failed: (glyphs->num_glyphs > 0)
```
What could cause this error?
**EDIT//** I have libpango1.0-0 installed. Both regular, common, and dev.

---

### Post by c_dog on 2005-04-10
How about gtk2-perl ? Looks like there a GObject call going on too.

---

### Post by Joh_ on 2005-04-11
[QUOTE=c_dog]How about gtk2-perl ? Looks like there a GObject call going on too.[/QUOTE]
 But, I was so sure I installed that yesterday. :o

Thanks it works now. :)

---

