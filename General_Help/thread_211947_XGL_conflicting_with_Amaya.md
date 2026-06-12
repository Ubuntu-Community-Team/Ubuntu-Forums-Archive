---
title: "XGL conflicting with Amaya?"
date: 2006-07-09
forum: General Help
---

### Post by pravuil on 2006-07-09
I installed XGL so I could use compiz but when I install amaya from the latest package I get this error when I try to start it up:

```
The program 'amaya' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 773 error_code 8 request_code 129 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
```

When I try to compile the latest Amaya source from cvs it says it requires either mesa or wxwidgets to be installed. I downloaded the wxwidgets source and compiled it correctly. Still wouldn't work. When using compiz I use the gdm.conf-custom edit to enable xgl during boot as stated in this thread [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl). I decided to remove the edits in the /etc/gdm/gdm.conf-custom file and after a reboot Amaya starts up as if nothing was wrong.

I ran Amaya from a terminal and it said that it's using mesa. Is there a way for XGL to run with mesa at the same time? Is there an alternative way to force WX instead of mesa when running Amaya?

I would really like to run Amaya within Compiz. [-o< If I can't then I would also like to know if there are any other alternatives out there similar to Macromedia's Contribute 3 other than an addon for firefox? If not I guess I'm stuck using NVU and gedit.

BTW, love the new design.=D>

---

