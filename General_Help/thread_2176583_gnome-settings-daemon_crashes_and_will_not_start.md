---
title: "gnome-settings-daemon crashes and will not start"
date: 2013-09-25
forum: General Help
---

### Post by MarshyTheKid on 2013-09-25
```
$ gnome-settings-daemon 
[1380092067,000,xklavier.c:xkl_engine_start_listen/] 	The backend does not require manual layout management - but it is provided by the application

(gnome-settings-daemon:14497): Gdk-ERROR **: The program 'gnome-settings-daemon' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 3110 error_code 8 request_code 131 minor_code 22)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the GDK_SYNCHRONIZE environment
   variable to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Trace/breakpoint trap

```
Any suggestions?  gconf-editor just had pointing-device under /apps/gnome-settings-daemon/plugins, so no xrandx to disable as suggested for other BadMatch crashes.

---

### Post by MarshyTheKid on 2013-09-28
Well luckily I have mate installed as well and can get it to kinda work. Just gotta get /usr/bin/mate-settings-daemon running then run the mate-control-center and then my settings can change, like adding a second monitor.

---

