---
title: "gnome-terminal not working??"
date: 2007-01-11
forum: General Help
---

### Post by ESPOiG on 2007-01-11
i dunno what happened but gnome-terminal doesnt work anymore, i reset the comp thinkin it was just a random problem but it still dont work, this is what it looks like when i run it in xterm

> user@ubuntu-linuxbox-2:~$ gnome-terminal
The program 'gnome-terminal' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadValue (integer parameter out of range for operation)'.
  (Details: serial 105 error_code 2 request_code 78 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by SkyIsFalling on 2007-01-11
I'm guessing you're using nvidia-glx?

[https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232](https://launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.17/+bug/58232)

It's a current bug, but there are some workarounds there that you may be interested in.

---

### Post by aysiu on 2007-01-11
[quote=error message]This probably reflects a bug in the program.[/quote] File a bug report?

---

### Post by ESPOiG on 2007-01-12
yeh im using nvidia-glx whats the workarounds plz

---

