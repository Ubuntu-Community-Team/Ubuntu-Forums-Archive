---
title: "vino-server crash on connect"
date: 2006-11-22
forum: General Help
---

### Post by tonygorg on 2006-11-22
Whenever I try to connect to my box using vnc I get:

anthony@byteripper:/usr/lib/vino$ ./vino-server
22/11/2006 12:47:53 PM Autoprobing TCP port
22/11/2006 12:47:53 PM Autoprobing selected port 5900
22/11/2006 12:47:53 PM Advertising security type: 'TLS' (18)
22/11/2006 12:47:53 PM Advertising authentication type: 'VNC Authentication' (2)
22/11/2006 12:47:53 PM Advertising security type: 'VNC Authentication' (2)
22/11/2006 12:48:41 PM Got connection from client 192.168.5.2
22/11/2006 12:48:41 PM   other clients:
The program 'vino-server' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadImplementation (server does not implement operation)'.
  (Details: serial 94 error_code 17 request_code 129 minor_code 5)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
anthony@byteripper:/usr/lib/vino$

-Dapper Drake 6.06
-also running XGL + compiz

I found a bug pertaining to XGL and vino on bugzilla and it said that they released a patch to fix it, however I do not understand the format of the patch. Do I have to recompile gnome with this code?

link - [https://launchpad.net/distros/ubuntu/+source/xserver-xgl/+bug/32641](https://launchpad.net/distros/ubuntu/+source/xserver-xgl/+bug/32641)

If that is the case, I think it would be much easier I to just install Edgy Eft if it contains the updated code. It also still crashes when I disable compiz in System-Preferences-Sessions-Startup Programs. Let me know what you guys think.

---

