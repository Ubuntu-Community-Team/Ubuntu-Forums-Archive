---
title: "Browsers crashing - segmentation fault?"
date: 2005-06-16
forum: General Help
---

### Post by matt on 2005-06-16
Certain websites have been constantly causing my browsers to either exit without warning or freeze so that I have to kill them. It seems to be the same sites that do this continually, although almost any site seems to freeze them at times.

The worst site for causing an exit without warning is [www.lawschooldiscussion.org/prelaw/](www.lawschooldiscussion.org/prelaw/)  The LSAT forum on that site seems to be the worst of all. I'm running Hoary with no backports...just official repo stuff. I've installed Flash and JRE too. Can't think of anything else.

I've tried these sites in both Firefox and Ephiphany, with the same result. When I run them from the command line, the output is:

Epiphany:

Destroy
The program 'epiphany' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadShmSeg (invalid shared segment parameter)'.
  (Details: serial 35 error_code 171 request_code 147 minor_code 2)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Firefox:

DestroyStream
Segmentation fault

I'm still pretty much a newbie...jumped to Linux with Warty last fall....any advice would be appreciated.

Cheers,
Matt.

---

### Post by Xian on 2005-06-16
[QUOTE=matt]The worst site for causing an exit without warning is [www.lawschooldiscussion.org/prelaw/](www.lawschooldiscussion.org/prelaw/)  The LSAT forum on that site seems to be the worst of all. I'm running Hoary with no backports...just official repo stuff. I've installed Flash and JRE too. Can't think of anything else.[/QUOTE]
You know, I don't run FF much but I do recall having it crash alot on sites that used flash banners like the one you linked. And that was with all the default plugs in place. The only way I got it to clear up was to actually go and download the Flash Player direct from the Macromedia website and install it straight from the command line.

---

### Post by matt on 2005-06-16
Thanks Xian...

I removed libflash-mozplugin and haven't had any crashes thus far (haven't been able to see any flash content either, obviously) but clearly it was flash that was causing the problem. I'll try installing it from Macromedia's site tomorrow and see if it is more stable.

---

