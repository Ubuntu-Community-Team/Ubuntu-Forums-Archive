---
title: "VNC port 5900?"
date: 2008-03-30
forum: General Help
---

### Post by bone2006 on 2008-03-30
I'm a little confused.  A friend of mine has Linux Minut and I have Kubuntu, I fired up the VNC viewer and was able to connect to his VNC server, but after disconnecting we weren't able to connect again.

My question is that I never did port forwarding on my router for port 5900, wasn't I supposed to?  I don't know why it even worked for 20 or 30 minutes before I manually disconnected.  

So why does it work even though I never open up any ports in iptables nor the router?  But now it's not working

---

### Post by chewearn on 2008-03-31
You don't have to open port, since you are making outgoing connections.
But, you friend needs to open port in his router, since he is operating a server (waiting for incoming connection).

---

