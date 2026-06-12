---
title: "Qt Designer crashes my X Server"
date: 2006-11-10
forum: General Help
---

### Post by fabiomargarido on 2006-11-10
Hey there,

I just installed Ubuntu Edgy today and started installing the applications I need from Synaptic. I intalled all of the Qt3 development packages, and every time I try to run Qt Designer, the splash screen appears and works correctly, but as soon as the program interface starts to show, the X Server instantly crashes and I get the GDM login screen again. No error messages, nothing.
I believe it's not related to Qt, cause I can run KPDF, Amarok and the application I developed with Qt Designer (in my previous Mandriva installation) without a problem. Qt Designer is so far the only application that has caused this.
Has anyone had similar problems or know how to workaround this? Any help would be greatly appreciated as I really need to use Qt Designer and really don't want to install another distro.
Let me know if you need additional info.
Thanks in advance.

Fabio Margarido

---

### Post by fabiomargarido on 2006-11-10
Just an update:

I tried to run Designer under strace, and the end of the output shows the following:

(...)
write(3, "5 \4\0V\10 \3E\0\0\0\311\0\33\0>\0\7\0<\10 \3V\10 \3D\0"...,
104) = 104
read(3, 0xbffc6c90, 32)                 = -1 EAGAIN (Resource
temporarily unavailable)
poll([{fd=3, events=POLLIN, revents=POLLIN|POLLHUP}], 1, -1) = 1
read(3, "", 32)                         = 0
write(2, "designer: Fatal IO error: client"..., 40) = 40
--- SIGHUP (Hangup) @ 0 (0) ---
+++ killed by SIGHUP +++

---

### Post by christhemonkey on 2006-11-10
Maybe you should file a bug report?


Here:
[https://launchpad.net/distros/ubuntu](https://launchpad.net/distros/ubuntu)


I dont know what you can do to help this situation.
How much RAM do you have?
What graphics card do you have?

---

### Post by fabiomargarido on 2006-11-10
The machine is a Pentium 3 750 MHz, 256 MB RAM and the graphics card is an onboard intel.

---

