---
title: "Gimp 2.10.18 crashing every time I cut or copy a selection"
date: 2020-10-22
forum: General Help
---

### Post by goemonburo on 2020-10-22
I'm trying to meet a delivery tomorrow (Friday) and opened up GIMP only to find that every darn time I cut or copy (whether using Cntl-x or -c OR the pulldown "Edit" menu options) the program crashes.  Desperate, I installed Glimpse Image Editor only to find the same thing happening there.

On another thread somewhere someone had a similar problem and had installed "CopyQ" on their machine, a clipboard manager.  Is there any chance Lubuntu 20.04LTS has something like that automatically installed and this is causing issues?  I have 40GB of Ram, so I don't think copying a 640x480px image is causing the RAM to max out.  I do not recall ever installing a clipboard manager.  Yet perhaps this is there by default?  Or LXQt has other settings that are causing issues?

Any help would be greatly appreciated.  I realize this may be a GIMP and not Ubuntu issue but perhaps someone out there knows what's going on.

---

### Post by norobro on 2020-10-22
Have you tried starting Gimp from the command line? Maybe some errors will show up and give us a hint as to what is going on.

---

### Post by goemonburo on 2020-10-22
Thank you, @norobro -- good idea.


me@home:~$ gimp
using gegl copy

(gimp:248888): Gdk-CRITICAL **: 22:06:25.414: IA__gdk_window_get_events: assertion 'GDK_IS_WINDOW (window)' failed

(gimp:248888): Gdk-CRITICAL **: 22:06:25.414: IA__gdk_window_set_events: assertion 'GDK_IS_WINDOW (window)' failed
The program 'gimp' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 95997 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

(script-fu:248910): LibGimpBase-WARNING **: 22:06:25.457: script-fu: gimp_wire_read(): error

---

### Post by norobro on 2020-10-22
Sorry, most anything involving Xorg is above my pay grade. Maybe someone else will be along who can help.

Meanwhile you could try posting on a Gimp forum: [https://gimp-forum.net/](https://gimp-forum.net/)

---

### Post by norobro on 2020-10-22
I run Ubuntu 20.04. Being a long time Qt programmer I was curious about LXQt and have it installed on this machine, although I have rarely used it.

It looks like "qlipper" clipboard manager is installed with LXQt. If it is running, try killing it and see if that helps. If I start "qlipper" in Ubuntu I get an icon in the top bar.

Gimp copy/paste works fine with or without "qlipper" running for me.

---

### Post by ActionParsnip on 2020-10-23
What is the output of
```

lsb_release -a; uname -a; apt-cache policy gimp

```

Also, if you make a new user and log in to the system as the new user is it the same?

---

