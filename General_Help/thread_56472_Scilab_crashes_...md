---
title: "Scilab crashes .."
date: 2005-08-12
forum: General Help
---

### Post by cnayak on 2005-08-12
I installed Scilab using apt-get. However on starting up scilab, I get the following error message:

[I] /usr/bin/scilab: line 31: /usr/lib/pvm3//lib/pvmgetarch: No such file or directory

(zterm:23237): Gdk-WARNING **: locale not supported by Xlib

(zterm:23237): Gdk-WARNING **: cannot set locale modifiers
cnayak@ubuntu:~$
(zterm:23237): ZVT-WARNING **: Cannot get required fonts from "monospace 13"

(zterm:23237): ZVT-WARNING **: Use "-*-*-*-*-*-*-13-*-*-*-*-*-*-*" XLFD fontname - some characters may not appear correctly


(zterm:23237): ZVT-WARNING **: Use "-*-*-*-*-*-*-0-*-*-*-*-*-*-*" XLFD fontname - some characters may not appear correctly


(zterm:23237): ZVT-CRITICAL **: file zvti18n.c: line 812 (zvt_term_get_xfontset): assertion `new_fontset != NULL' failed

(zterm:23237): ZVT-WARNING **: Failed to load any required font, so crash will occur..check X11 font pathes and etc/pangox.alias file


(zterm:23237): ZVT-WARNING **: Cannot get required fonts from "monospace 13"

(zterm:23237): ZVT-WARNING **: Use "-*-*-*-*-*-*-13-*-*-*-*-*-*-*" XLFD fontname - some characters may not appear correctly


(zterm:23237): ZVT-WARNING **: Use "-*-*-*-*-*-*-0-*-*-*-*-*-*-*" XLFD fontname - some characters may not appear correctly


(zterm:23237): ZVT-CRITICAL **: file zvti18n.c: line 812 (zvt_term_get_xfontset): assertion `new_fontset != NULL' failed

(zterm:23237): ZVT-WARNING **: Failed to load any required font, so crash will occur..check X11 font pathes and etc/pangox.alias file
[/I]
 
  I guess some fonts are missing. What additional packages do I have to install?

---

### Post by tasuki on 2005-11-23
just found your post looking for the solution of the same problem... :-(

---

### Post by jrib on 2005-11-23
Well I didn't get those errors a few weeks ago but I did get strange (unreadable) fonts in my scilab (a bug that has been reported on launchpad).  I ended up installing scilab from the official site and that worked well.  If you don't get any help with this error you could always try that.

---

