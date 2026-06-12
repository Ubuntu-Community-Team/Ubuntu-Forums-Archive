---
title: "Running OpenGL from xRDP"
date: 2012-10-24
forum: General Help
---

### Post by essidy01 on 2012-10-24
I hope this is the right forum to post this in; it didn't really seem to fit with Networking or Desktop environments, but if it's better suited elsewhere, let me know!

I'm trying to set up a lab on a college campus that I work at to allow students to use RDP (specifically, we're using xRDP) to access the machines. Everything works just fine for them as they're able to see the desktop environment, but we run into an issue when we try to run programs we've compiled in our Graphics design course. This is the error it gives:

```

freeglut (./myprogram):  ERROR:  Internal error <FBConfig with necessary capabilities not found> in function fgOpenWindow
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  4 (X_DestroyWindow)
  Resource id in failed request:  0x0
  Serial number of failed request:  21
  Current serial number in output stream:  24


```

When we're running the program from SSH using
```
ssh -X -Y username@workstation.site.edu
```
it all works fine and the OpenGL program compiles and displays fine once we've typed ```
export LIBGL_ALWAYS_INDIRECT=1
``` into the terminal window. However, this doesn't work for me when I'm using RDP. 

Can anyone please provide some insight on how I might get OpenGL to work here in this setup? I'd really appreciate any help. Thanks in advance. :)

I forgot to mention: We're running 10.04 currently (still testing 12.04).

---

### Post by essidy01 on 2012-10-28
Any ideas from anyone? I'm willing to try most anything at this point.

---

### Post by keivanmoradi on 2012-12-14
Hi.
You should configure your vnc session with X11VNC (not TightVNC, not TigerVNC, not realVNC or else) and then connect to the server with XRDP. you can find a very good information about how to configure x11vnc in gentoo wiki.
[http://en.gentoo-wiki.com/wiki/X11VNC](http://en.gentoo-wiki.com/wiki/X11VNC)

---

