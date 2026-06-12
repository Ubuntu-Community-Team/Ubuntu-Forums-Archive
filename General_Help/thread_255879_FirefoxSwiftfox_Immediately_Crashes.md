---
title: "Firefox/Swiftfox Immediately Crashes"
date: 2006-09-12
forum: General Help
---

### Post by kalbir on 2006-09-12
Hey everyone,

I've had this problem with firefox/swiftfox crashing about 10-30seconds after starting it up. When I start it in terminal I get:

> LoadPlugin: failed to initialize shared library /usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so [/usr/lib/Adobe/Acrobat7.0/Browser/intellinux/nppdf.so: undefined symbol: XtCalloc]
The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 145 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)


Tried running firefox --synch but to no avail. 

I installed Aiglx/Compix on a clean Dapper installation and then used Automatix to install some plugins for firefox and the swiftfox browser. Any ideas for what to do?

Thanks,

Kalbir

---

### Post by guine on 2006-09-12
Well if nobody gives any suggestions on how to fix firefox you can use the beta 2 for firefox 2
[http://www.mozilla.org/projects/bonecho/all-beta.html]("http://http://www.mozilla.org/projects/bonecho/all-beta.html")
I was unable to use firefox too after using automatix and was never able to fix it but the beta 2 has been working fine for me.

---

### Post by kalbir on 2006-09-13
Maybe it is an automatix problem then... 

Thanks for the tip- I think I'll have to switch to the beta as I just can't get used to Opera

---

