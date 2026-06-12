---
title: "Exaile not working after upgrade"
date: 2007-06-26
forum: General Help
---

### Post by rafaelcapanema on 2007-06-26
Hey,

Just upgraded Exaile from 0.2.9 to 0.2.10, but now it won't launch anymore. Tried running it from the terminal and got this message:

> /usr/share/exaile/xl/xlmisc.py:1717: GtkWarning: gdk_drawable_set_colormap: assertion `cmap == NULL || gdk_drawable_get_depth (drawable) == cmap->visual->depth' failed
  pixmap.set_colormap(colormap)
/usr/share/exaile/xl/xlmisc.py:1740: GtkWarning: Using Cairo rendering requires the drawable argument to
have a specified colormap. All windows have a colormap,
however, pixmaps only have colormap by default if they
were created with a non-NULL window argument. Otherwise
a colormap must be set on them with gdk_drawable_set_colormap
  pixmap.draw_layout(gc, x, y, layout)
/usr/share/exaile/xl/xlmisc.py:1740: GtkWarning: No colormap in gc_get_foreground
  pixmap.draw_layout(gc, x, y, layout)
/usr/share/exaile/xl/xlmisc.py:1744: GtkWarning: gdkpixbuf-drawable.c:1255: Depth of the source drawable is 24 where as the visual depth of the colormap passed is 16
  0, width, height)
Traceback (most recent call last):
  File "exaile.py", line 2635, in <module>
    main()
  File "exaile.py", line 2627, in main
    exaile = ExaileWindow(options, fr)
  File "exaile.py", line 202, in __init__
    self.setup_left()
  File "exaile.py", line 1036, in setup_left
    self.collection_panel = panels.CollectionPanel(self)
  File "/usr/share/exaile/xl/panels.py", line 235, in __init__
    self.setup_widgets()
  File "/usr/share/exaile/xl/panels.py", line 257, in setup_widgets
    self.create_popup()
  File "/usr/share/exaile/xl/panels.py", line 352, in create_popup
    icon_set = gtk.IconSet(pixbuf)
TypeError: pixbuf should be a GdkPixbuf

Help appreciated.
Cheers.

---

### Post by kpkeerthi on 2007-06-26
try doing a clean install. 
```

sudo aptitude purge exaile

```

```

rm -rf ~/.exaile

```

```
sudo aptitude install exaile
```
... and any plugins you may require.

---

### Post by adzik on 2007-09-11
I have just come across this issue myself and I think I know the basic cause.
I was already using version 0.2.10 successfully, but I had to drop my video / X bit depth from 24 to 16 for some testing purposes and that is when it stopped working. The output refers to this:
> /usr/share/exaile/xl/xlmisc.py:1744: GtkWarning: gdkpixbuf-drawable.c:1255: Depth of the source drawable is 24 where as the visual depth of the colormap passed is 16
I have no clue how to fix this as it may be a bug?? 
But in the mean time setting your bit depth to 24 in your xorg.conf file should get it working again... at least it did for me.
You can also trying compiling from source. 
If I find out more I will post.
Good luck!

BTW: I attemped purge and reinstall a couple times with no success.

---

### Post by Astronomy_Nick on 2007-09-21
Thanks for that analysis of the error message. I was getting the exact same error and editing the default depth of my monitor in xorg.conf has solved the problem.

---

