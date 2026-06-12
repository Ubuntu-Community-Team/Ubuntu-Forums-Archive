---
title: "Msttcorefonts and Defoma boot problem"
date: 2008-01-27
forum: General Help
---

### Post by Lanky Juggler on 2008-01-27
Hey!  I've recently given linux to a hallmate at college.  By happenstance, his windows partition got borked, so we just set aside an empty partition and installed 7.04 and upgraded immediately to 7.10.  We've had a few problems, but none has been as persistant as one with MSTTcorefonts.

At first, it couldn't fully install the file, and apt-get would shoot out an error message everytime we tried installing it or removing it.  Eventually, we got this error where Ubuntu would boot, orange loady bar and all, but then before X really kicked in, it would bring up what we have called 'box errors.'  Essentially, a window against a black background with boxes where there should be characters, presumably because it can't actually find any fonts.  We reinstalled 7.04 (a CD I have used successfully in the past) and upgraded again, and had none of the earlier partially installed problems with msttcore-fonts that we used to have.  Several days later, however, upon booting the box errors started up again! the other ttys are fully functional.

The final time the computer was used before the boot errors came up, it provided the following error:

"Msttcorefonts uses the DEbian FOnt MAnager (defoma).  If you wish to use the fonts provided by this package under the X Window System, you must configure it to use defoma fonts.

The easiest way to do so is to use the x-ttcitfont-conf package.  For more information, install the x-ttcidfont-conf parage and consult its documentation under /usr/share/doc/x-ttcidfont-conf.

For uses for msttcorefonts not related to the X Window Systemn (e.g. printing) this is not required"

Any ideas, guys?  I'll be really appreciatory if you can point us in the right direction!

Thanks

---

### Post by yabbadabbadont on 2008-01-27
Do you have x-ttcidfont-conf installed?  If not, install it.

---

### Post by Lanky Juggler on 2008-01-27
We have installed it, yes.  I'll fiddle aroudn with it a bit more and see what comes up.

---

### Post by Lanky Juggler on 2008-01-27
Hey! An update...

We dug up the time things stopped working in the syslog.  The error message we're really looking at (which happened shortly before it failed to boot) is

Pango-WARNING: No builtin or dynamically loaded modules were found.  Pango will not work correctly.  This probably means there was an error in the creation of:  '/etc/pango/pango.modules' You should create this file by running pango-querymodules.
Pango-WARNING: pango_shape called with bad font, expect ugly output
Pango-WARNING: pango_font_get_glyph_extents called with null font argument, expect ugly output
Pango-WARNING: pango_font_get_metrics called with null font argument, expect ugly output
Pango-WARNING: pango_cairo_font_get_scaled_font called with bad font, expect ugly output


This error message repeats several times without change.  The computer does not recognize 'pango-querymodules,' although it does recognize pango.  Apropro digs up a command 'update-pangox-aliases' so I'm assuming it is installed.  We ran it to no effect.

---

### Post by yabbadabbadont on 2008-01-27
I'm not running ubuntu currently, so I'm not sure about the package names.  What you might try is forcing a reinstall of pango, msttcorefonts, and x-ttcidfont-conf.  (in that order)

In a terminal window, run ```
sudo dpkg-reconfigure pango
```  and so on for each of the others.  Of course, put it the correct package name for pango.  You could also just select each package in synaptic and re-install from there.  That might be the easiest way.  Be sure to check the text box log of the installation though for any warnings.

---

