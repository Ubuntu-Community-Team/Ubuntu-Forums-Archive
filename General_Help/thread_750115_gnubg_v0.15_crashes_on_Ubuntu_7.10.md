---
title: "gnubg v0.15 crashes on Ubuntu 7.10"
date: 2008-04-09
forum: General Help
---

### Post by fs005 on 2008-04-09
Hello,

when i try to change the default-board in gnubg by klicking on "Settings->Appearance", the programm crashes with the following error(everytime; doesn't matter if i'm using 2D or 3D-mode):

```

The program 'gnubg' received an X Window System error.
This probably reflects a bug in the program.
The error was 'GLXBadContext'.
  (Details: serial 3977 error_code 154 request_code 143 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I'using gnubg v0.15 on Ubuntu 7.10 (X Window System Version 1.3.0,"Intel Corporation 82865G Integrated Graphics";driver is "intel").

I also uploaded the programm dependencies and my xor.0.log-file, just in case it might be useful: [http://ubuntuusers.de/paste/165973/](http://ubuntuusers.de/paste/165973/)

thanks for looking!
fs005

---

