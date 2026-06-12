---
title: "Compiz, 8.04 and X1950PRO, worked fine but now..."
date: 2008-06-23
forum: General Help
---

### Post by RubberSoul on 2008-06-23
I have this hardware, and everything was fine in my Hardy Heron, but a few days from now, I cant enable Compiz anymore... My system is updated, i've tried to install and reinstall video drivers, but nothing works... Please help.

My fglrxinfo is:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.1.7412 Release

And when i run compiz --replace i got this:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 1002:7280 (rev 9a) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
Window manager warning: Log level 8: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed

Please help. I love Compiz, thats my first time in linux, my hardware is not so compatible (ATI X1950Pro, Creative X-FI platinum fatality, Logitech G9), thats a headache for me... =[

---

### Post by RubberSoul on 2008-06-23
Disabled Metacity compositing manager (thats it?!?!), and Compiz works fine again! Thanks anyway, hope it helps some other people...

---

