---
title: "Gmail crashes Firefox 2.0 (gecko error)"
date: 2006-11-09
forum: General Help
---

### Post by CheeseEatingBulldog on 2006-11-09
I have a vaio laptop which I updated to Edgy and with it to Firefox 2.0. Now everytime I log onto my gmail account firefox just dies and vanishes. So find out what was happening I ran it in a terminal with the following result: 

The program 'Gecko' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 118 error_code 8 request_code 144 minor_code 3)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I have googled about and disabled composite in my xorg but to no avail, it only dies on gmail. 

I only have 4 extensions installed (adblock filterset, adblock, downthemall and gmail notifier). I run in 16 bit as my chipset otherwise won't do dri. (if that is relevant)

I have gotten it to work by launching firefox from the terminal using:

XLIB_SKIP_ARGB_VISUALS=1 ; firefox

This was from launchpad and apparently hides composite visuals, but I can't find how to set that in about:config so that I don't have to run firefox from the terminal each time.

Anybody have an idea how to solve this?

=======================EDIT

On a last ditch attempt I ran Automatix2 and installed flashplugin, which was the beta9 and it now works....weird.

---

### Post by Gen2ly on 2007-01-07
nod, gmail
sourceforge download page
etc

---

