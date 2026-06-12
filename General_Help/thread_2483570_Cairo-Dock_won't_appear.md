---
title: "Cairo-Dock won't appear"
date: 2023-02-03
forum: General Help
---

### Post by SciGuy1872 on 2023-02-03
Hi.  I have tried the terminal command to purge cairo dock, restarting, then going to terminal and entering the install command.  I have also tried to go to other panels with the Mate Tweak utility and typing from the menu cairo-dock, but the dock still does not appear.  I have also tried going to Synaptic.

---

### Post by SciGuy1872 on 2023-02-03
Here is more info:

> anthony@anthony-OptiPlex-9010:~$ cairo-dock -f
warning :  (/build/cairo-dock-XfXg2O/cairo-dock-3.4.1/src/implementations/cairo-dock-egl.c:gldi_register_egl_backend:232)  
  Cairo-Dock was not built with EGL support

 ============================================================================
    Cairo-Dock version : 3.4.1
    Compiled date      : May 24 2018 23:52:39
    Built with GTK     : 3.22
    Running with OpenGL: 1
 ============================================================================

gldi_managers_get_config: assertion 'pKeyFile != NULL' failed
warning :  (/build/cairo-dock-XfXg2O/cairo-dock-3.4.1/src/gldit/cairo-dock-image-buffer.c:cairo_dock_load_image_buffer_from_surface:162)  
  An image has an invalid size, will not be loaded.
g_file_test: assertion 'filename != NULL' failed
g_file_test: assertion 'filename != NULL' failed

(cairo-dock:6634): Gtk-WARNING **: 01:59:16.920: Theme parsing error: <data>:7:1467: The :insensitive pseudo-class is deprecated. Use :disabled instead.

(cairo-dock:6634): Gtk-WARNING **: 01:59:16.921: Theme parsing error: <data>:7:3649: The :inconsistent pseudo-class is deprecated. Use :indeterminate instead.
warning :  (/build/cairo-dock-XfXg2O/cairo-dock-3.4.1/src/gldit/cairo-dock-image-buffer.c:cairo_dock_load_image_buffer_from_surface:162)  
  An image has an invalid size, will not be loaded.
warning :  (/build/cairo-dock-XfXg2O/cairo-dock-3.4.1/src/gldit/cairo-dock-image-buffer.c:cairo_dock_load_image_buffer_from_surface:162)  
  An image has an invalid size, will not be loaded.
^Z
[1]+  Stopped                 cairo-dock -f



---

### Post by MAFoElffen on 2023-02-03
Am I confused? Or do you have this thread marked as "Solved"? I don't see your solution...

---

### Post by SciGuy1872 on 2023-02-03
Hi.  I solved the Cairo dock myself after reading about the options to launch the program with.   In the terminal, I entered "cairo-dock -f" to start safe mode, and then the dock appeared.  After the dock was visible, I went to "Themes"  and chose another theme that I had saved.  After these steps, I no longer had a problem with Cairo dock not appearing--whatever theme I happened to click on earlier (that was mine) had an error.  Yeah, there are a lot of options to start the program with.  [https://www.huge-man-linux.net/man1/cairo-dock.html](https://www.huge-man-linux.net/man1/cairo-dock.html)  Sorry for the confusion.

---

### Post by MAFoElffen on 2023-02-04
Now I am not confused. That was actually a very helpful solution for other's to find to help them with their similar problems. Thank you for sharing that.

---

