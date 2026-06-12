---
title: "Login Graphically?"
date: 2008-03-17
forum: General Help
---

### Post by jacensolo on 2008-03-17
I have a file server and got ssh working. The server is just that, a server with no gui. It has 8 scsi drives but only a 500mhz cpu. I want some kind of X but not on the server. Is there away to login to the server with all of the gui processing on the client side? That way for the server it would almost be like a ssh session. On one of my desktop pc's (which doesn't have network access now, only under windows due to a new adapter) I tried to get xdmcp working but I'm not sure if that's what I need.

Basically install fluxbox or something on the client and talk to the server via ssh so the server doesn't have performance issues.

---

### Post by Cyanic420 on 2008-03-17
If you install X windows on the client, you can connect xterm via ssh and run your gui apps on the client. Well sort of, you will still take a processing hit on the server, as the app is running on the server, but displayed on the client. Try it and see what kind of hit you take. It may be acceptable.

---

### Post by jacensolo on 2008-03-18
> **Cyanic420 said:**
> If you install X windows on the client, you can connect xterm via ssh and run your gui apps on the client. Well sort of, you will still take a processing hit on the server, as the app is running on the server, but displayed on the client. Try it and see what kind of hit you take. It may be acceptable.

Is this possible on a windows machine?

---

### Post by Nepherte on 2008-03-18
It is possible to graphically access the linux server from a windows machine. You'll need a ssh client and a Xserver.

---

