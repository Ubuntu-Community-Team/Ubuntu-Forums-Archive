---
title: "Themes MADness!!!"
date: 2008-05-28
forum: General Help
---

### Post by sithpigeon on 2008-05-28
Ok, I'm am having the hardest time getting themes to my gnome desktop and its driving me crazy because I'm stuck with the ugliest one ever! Every time I try to install a new theme it says "file format is incorrect" and all my old themes have since disappeared. The only things I changed were customizing the pre-installed themes and enabling my restricted nvidia driver (which I did after the themes went crazy. I'm completely stuck and have tried several applications such as gnome art to install new themes buck all I get are more errors. If I need to install somethings special or something please tell me cause this is really starting to bug me.

---

### Post by Forlong on 2008-05-29
Run ```
gnome-appearance-properties
``` in a terminal and look for any error messages.

Also, when there's a problem installing a theme, try to unpack the archive and drag&drop the folder into the Appearances Preferences window.

---

### Post by sithpigeon on 2008-05-29
ok ran that and got this in terminal

```
(gnome-appearance-properties:5578): libglade-WARNING **: Error loading image: Couldn't recognize the image file format for file '/usr/share/gnome-control-center/pixmaps/visual-effects_none.svg'

(gnome-appearance-properties:5578): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(gnome-appearance-properties:5578): libglade-WARNING **: Error loading image: Couldn't recognize the image file format for file '/usr/share/gnome-control-center/pixmaps/visual-effects_normal.svg'

(gnome-appearance-properties:5578): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(gnome-appearance-properties:5578): libglade-WARNING **: Error loading image: Couldn't recognize the image file format for file '/usr/share/gnome-control-center/pixmaps/visual-effects_extra.svg'

(gnome-appearance-properties:5578): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(gnome-appearance-properties:5578): libglade-WARNING **: Error loading image: Couldn't recognize the image file format for file '/usr/share/gnome-control-center/pixmaps/visual-effects_custom.svg'

(gnome-appearance-properties:5578): libglade-WARNING **: could not convert string to type `GdkPixbuf' for property `pixbuf'

(gnome-appearance-properties:5578): capplet-common-WARNING **: Could not open file "(null)"

(gnome-appearance-properties:5578): appearance-properties-WARNING **: Unknown Tag: comment


(gnome-appearance-properties:5578): appearance-properties-WARNING **: Unknown Tag: comment


(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_option: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_option: assertion `GDK_IS_PIXBUF (pixbuf)' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_bits_per_sample: assertion `pixbuf != NULL' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_width: assertion `pixbuf != NULL' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_height: assertion `pixbuf != NULL' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_rowstride: assertion `pixbuf != NULL' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_has_alpha: assertion `pixbuf != NULL' failed

(gnome-appearance-properties:5578): GdkPixbuf-CRITICAL **: gdk_pixbuf_get_pixels: assertion `pixbuf != NULL' failed

(gnome-appearance-properties:5578): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
```

---

