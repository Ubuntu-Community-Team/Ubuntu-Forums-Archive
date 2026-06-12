---
title: "Gxine opens and crashes"
date: 2007-08-04
forum: General Help
---

### Post by kdarkentity on 2007-08-04
well here it is... one day gxine stopped woking... im not sure why... i tried reinstalling it... no change... and below is my terminal output.... help plz


kevin@kevin-laptop:~$ gxine
lirc: cannot initialise - disabling remote control
lirc: maybe lircd isn't running or you can't connect to the socket?
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 403 error_code 11 request_code 141 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by TBerben on 2007-08-04
It appears to be [this](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-i810/+bug/49360) bug. The bug apparently exists in X.org

---

### Post by kdarkentity on 2007-08-05
hmm ...well i read through that article ...but i couldnt really figure out what i can do to fix it tho... the distro it mentions in that entire article is dapper and im running fiesty fawn ...sooo

---

