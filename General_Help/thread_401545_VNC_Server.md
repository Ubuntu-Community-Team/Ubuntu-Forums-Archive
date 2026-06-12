---
title: "VNC Server"
date: 2007-04-04
forum: General Help
---

### Post by stuffradio on 2007-04-04
Hi,

trying to get Tightvnc server to work... but don't know how to set it up, etc.

---

### Post by se2131 on 2007-04-05
You'll need to install x11vnc first

To protect the server, you should set up a password file.  Do this by x11vnc -storepasswd.  Then you can start it by using the command: x11vnc -forever -usepw.  The forever option keeps the server running after a connection has been made.

I think the password can also be set up or used using -rfbauth, but I haven't used it (you should still look into it, I just haven't cared enough to bother changing what works)

---

