---
title: "zinf problems"
date: 2006-12-18
forum: General Help
---

### Post by diatribe on 2006-12-18
I am running feisty fawn with xfce 4 and can get zinf to install fine, but it will not run.  Output reads as follows:

diat@ebirtaid:~$ zinf

(<unknown>:8101): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:8101): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:8101): Gdk-WARNING **: Attempt to draw a drawable with depth 24 to a drawable with depth 32

(<unknown>:8101): Gdk-CRITICAL **: gdk_window_set_back_pixmap: assertion `pixmap == NULL || gdk_drawable_get_depth (window) == gdk_drawable_get_depth (pixmap)' failed
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 343 error_code 8 request_code 62 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
diat@ebirtaid:~$ 


any ideas?

---

### Post by alef13 on 2008-03-13
if you export XLIB_SKIP_ARGB_VISUALS=1 before running zinf, it works. However, it crashes when you try to change theme.

---

