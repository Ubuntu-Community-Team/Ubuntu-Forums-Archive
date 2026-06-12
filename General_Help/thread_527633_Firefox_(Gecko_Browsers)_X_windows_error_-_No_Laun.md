---
title: "Firefox (Gecko Browsers) X windows error - No Launchy! :("
date: 2007-08-16
forum: General Help
---

### Post by promet on 2007-08-16
Hello,

I have come home today to find that, mysteriously, Firefox (actually no "Gecko-based" browser i.e. firefox, iceweasel, etc.) will launch on my Feisty install. 

Yesterday, smooth as silk, today crazy un-launchability. When run from the command line I get the following error:

```

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadDrawable (invalid Pixmap or Window parameter)'.
  (Details: serial 776 error_code 9 request_code 66 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I've tried Iceweasel, I've removed and re-installed Firefox, done "dpkg-reconfigure xserver-xorg" and a variety of other arcane solutions but, no love.

There's seems to be little in the way of Googlisms on this either. Please lend a helping hand if you can. Opera just doesn't fill me with confidence, if you know what I'm saying...

Thanks

Promet

---

