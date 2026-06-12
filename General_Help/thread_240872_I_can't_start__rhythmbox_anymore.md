---
title: "I can't start  rhythmbox anymore ??"
date: 2006-08-21
forum: General Help
---

### Post by balki2005 on 2006-08-21
Hello,

I don't know  what happen, but  I can't start rhythmbox anymore. when I try  from commandline I recieve this error:
thundermaster@thunderdragon:~/public_html$ /home/thundermaster/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:943: Unable to locate image file in pixmap_path: "focus_button.svg"
/home/thundermaster/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:945: Background image options specified without filename
/home/thundermaster/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:1029: Unable to locate image file in pixmap_path: "focus_button.svg"
/home/thundermaster/.themes/Polycarbonate-Dark/gtk-2.0/gtkrc:1031: Background image options specified without filename
(rhythmbox:5863): GdkPixbuf-CRITICAL **: gdk_pixbuf_new_from_file: assertion `filename != NULL' failed

(rhythmbox:5863): Rhythmbox-WARNING **: Unable to load icon media-eject

(rhythmbox:5863): Rhythmbox-WARNING **: Unable to start mDNS browsing
The program 'rhythmbox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 3015 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

can somebody help me  ?

thanks in advance,

balki2005

---

### Post by Perfect Storm on 2006-08-22
Looks like a theme problem. Try switch theme.

---

