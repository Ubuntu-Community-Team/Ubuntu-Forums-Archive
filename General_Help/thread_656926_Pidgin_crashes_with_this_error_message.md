---
title: "Pidgin crashes with this error message"
date: 2008-01-03
forum: General Help
---

### Post by Sonja on 2008-01-03
sonja@Sonja:~$ pidgin
The program 'pidgin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAtom (invalid Atom parameter)'.
  (Details: serial 11 error_code 5 request_code 20 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

How can I fix it? :(

---

### Post by Sonja on 2008-01-03
Hm, I did this and it fixed it!

sonja@Sonja:/usr/lib/purple-2$ sudo rm libskype.so

I guess the Skype plugin I tried downloading is buggy.

---

