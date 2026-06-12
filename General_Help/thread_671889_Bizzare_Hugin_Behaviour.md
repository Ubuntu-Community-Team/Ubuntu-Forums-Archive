---
title: "Bizzare Hugin Behaviour"
date: 2008-01-19
forum: General Help
---

### Post by CharlesBasengaKiyanda on 2008-01-19
I'm on ubuntu 7.10 32 bit. I had installed hugin through the ADD/Remove program without a problem. It worked, several weeks ago. I just tried starting hugin again this time and it crashed. I tried rebooting the Xserver and the computer as a whole, but it didn't help. I uninstalled and reinstalled hugin, but the same behaviour still occurs. When I try to start hugin from the command line (using the command 'hugin'), I get the following error:

The program 'hugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 795 error_code 11 request_code 147 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Any ideas on why that is? I didn't delete random files anywhere. I'm tempted to think that something has broken hugin, but I can't find anyone complaining in the form or anywhere else, so I find that bizarre.

Charles

---

### Post by CharlesBasengaKiyanda on 2008-01-19
Nevermind! There was an update to xserver-xorg-core coming through and it fixed the problem.

Charles

---

