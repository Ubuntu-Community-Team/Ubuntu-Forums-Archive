---
title: "How do I install a Gimp Plugin?"
date: 2007-01-03
forum: General Help
---

### Post by oliwally on 2007-01-03
I'm trying to install a Gimp plugins according to the plugin instructions, but I'm not having any luck. The plugins I'm trying to install (exif browser and refocus-it) both have similar instructions to configure, make and make install. Although there is some action in the Konsole, in the end it doesn't seem to be installed. 

Where am I going wrong? Why are the instructions listed with the plugin not working?

---

### Post by syxbit on 2007-01-03
[http://ubuntuforums.org/showthread.php?t=322285](http://ubuntuforums.org/showthread.php?t=322285)

---

### Post by oliwally on 2007-01-04
> **syxbit said:**
> [http://ubuntuforums.org/showthread.php?t=322285](http://ubuntuforums.org/showthread.php?t=322285)

Thanks for that. I've tried some of the suggestions listed at this link and also at the gimp site ([http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install](http://docs.gimp.org/en/concepts-intermediate.html#gimp-plugins-install)) but I'm not having any success. 

To be honest, I'm finding it difficult to follow the instructions because the installation paths are not clear to me. Where, for example, is the "main system GIMP directory"? (according to docs.gimp.org "Some plugins (specifically those based on the GIMP  Plugin Template) are designed to be installed in the main system GIMP directory, rather than your home directory. "). A system search led me to several locations where gimp may be installed, with several locations of plugin folders. Which is the main one? Where do I install a "complex plugin"?

Isn't the an easier or clearer way?

---

### Post by _simon_ on 2007-01-04
When I "install" a gimp plugin all I do is place it in ~/.gimp-2.2/plug-ins/

To be clear, in your Home Folder, view hidden files and look for .gimp-2.2 (it may have a slightly different name depending on version) and just place the plugin in the /plugins folder.

If you have The Gimp open then just restart it.

The new plugins are located in your Filters Menu.

---

