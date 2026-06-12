---
title: "VNC local loopback enable"
date: 2008-01-16
forum: General Help
---

### Post by saviour on 2008-01-16
Hi,

I'm using a reverse vnc connection forwarding remote port 5900 back to my Ubuntu desktop. When I try to connect to 127.0.0.1  with xvncviewer I get an error saying local loopback connections are disabled. My question here is how do I enable local loopback connections? I searched all man pages with no success. The remote windows vnc server has local loopback enabled.

---

### Post by punkeyfunky on 2008-06-30
If, like me, you're using tightVNC (and possibly others?) you need to explicitly configure the VNC server to allow loopback connections.

-Lee

---

