---
title: "Custom icon in menu"
date: 2007-10-19
forum: General Help
---

### Post by Fraoch on 2007-10-19
In Feisty, I installed a custom program that didn't add itself to the Applications menu.  I just added it manually.  It used an .xpm icon and it displayed fine.

However, in Gutsy, I can add the program but I can't select an .xpm icon, it only wants me to select an .svg icon, and I have no way to convert .xpm to .svg.

Any advice?

---

### Post by deminy on 2008-01-12
You can simply copy the xpm file to directory /usr/share/pixmaps/ and use the icon under directory /usr/share/pixmaps/ .

Or, if you really want to convert xpm file to svg file, here is an article I just read. Hope it helps:

How to convert pixel (raster) files (png) to vector graphic (svg) on Linux
[http://sysblogd.wordpress.com/2007/09/30/how-to-convert-pixel-files-png-to-vector-graphic-svg-on-linux/](http://sysblogd.wordpress.com/2007/09/30/how-to-convert-pixel-files-png-to-vector-graphic-svg-on-linux/)

The tool (inkscape) is a GUI tool, so you can easily open the xpm file in the tool and then save it as a PLAIN svg file.

Good luck.

---

### Post by Fraoch on 2008-02-05
It turned out to be a bit of an inconsistency in how I expected to open /usr/share/pixmaps, it works a little differently than browsing for a file.

You can't browse into /usr/share/pixmaps, it won't show you the icons.  Instead browse into /usr/share, select pixmaps and press the "Open" button.  Only then will it show the icons in the directory, not if you browse into the directory.

---

