---
title: "How to connect to 12.04 from windows?"
date: 2013-01-04
forum: General Help
---

### Post by rva1945 on 2013-01-04
I installed RealVNC in the W7 Pc at the office.

I have a DynDNS host service, it's available, in the router configuragion page, the connection is ok (Succeed!), I can even ping home (U 12.04) from that PC.

But the VNC viewer doesn't connect. Is there any tutorial to make this work, I mean, to make ubuntu to be a VNC server?

Thanks

---

### Post by windscape on 2013-01-04
Hi,

Searching the forums before creating a new thread is generally a good idea. This question has already been asked and answered here: [http://ubuntuforums.org/showthread.php?t=2100574](http://ubuntuforums.org/showthread.php?t=2100574)

Bottom line, NX is recommended when connecting across the Internet, as it does encryption whereas VNC does not. NX is not open source and setting it up can be tricky. To use VNC across the Internet, you will need to open a port in your router and forward it to your Ubuntu PC. You will also need to find "Desktop Sharing" in Ubuntu and enable it. 

[http://portforward.com/](http://portforward.com/) can help with the port forwarding part in the router, after Desktop Sharing is enabled in Ubuntu.

---

### Post by steeldriver on 2013-01-04
If you *are* going to use VNC over a public network then you should ssh-tunnel it - you can use putty at the Windows end to set up the tunnel

---

