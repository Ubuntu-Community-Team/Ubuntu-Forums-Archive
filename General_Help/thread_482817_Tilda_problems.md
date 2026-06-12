---
title: "Tilda problems"
date: 2007-06-24
forum: General Help
---

### Post by black_knight on 2007-06-24
The very first day I installed Ubuntu I also installed Tilda via sudo apt-get install tilda

the next day Tilda refuses to work even the slightest.
I tried uninstalling and reinstalling but the settings are saved and the error persists.
the error shows on the launching of tilda

> (tilda:8623): Gtk-CRITICAL **: gtk_window_resize: assertion `height > 0' failed
The program 'tilda' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAccess (attempt to access private resource denied)'.
  (Details: serial 11 error_code 10 request_code 33 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

so does anyone know how to delete the saved settings or what do I do.

---

### Post by aussiedini on 2007-06-24
It creates a .tilda directory in your home directory when you start. Try deleting that

---

