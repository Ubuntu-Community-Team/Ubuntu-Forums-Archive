---
title: "xorg with composite enabled causes firefox crash"
date: 2005-05-20
forum: General Help
---

### Post by f.prisson on 2005-05-20
Hi everybody,

if I have composite enabled in xorg.conf and start epiphany or firefox with java and javascript enabled, the browsers crash with the following error:

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 117 error_code 8 request_code 147 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

If I disable either composite or browser java functionality everything works fine.

xorg version: 6.8.2, firefox version: 1.0.2

Has anybody seen this error?

---

### Post by nad on 2005-05-20
If you are using the ATI graphics driver, composite extension functionallity is considered experimental.

Please see the man page for your video driver module.

---

### Post by f.prisson on 2005-05-20
I use an ASUS M2400N with Intel 855GM chipset here. For me the error looks like a bug, but I hoped anybody had the same problem and a solution.

---

### Post by f.prisson on 2005-05-22
OK, I found a bug in bugzilla which sounds as if I'm suffering about it. Added some comment with more output. It's a pity, because I need Java and love composite  :?

---

