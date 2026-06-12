---
title: "Vnc _without ssh tunneling_"
date: 2016-07-12
forum: General Help
---

### Post by bensode on 2016-07-12
Kinda aggravated.  I want VNC to listen on it's IP, not localhost 127.0.0.1.  I have to connect to several X session running elsewhere behind VPN and currently using Windows and not interested in tunneling through putty or tunneling at all.  Googling top 5 results all yield how to connect with SSH, which is not what I want to do.  Found a CENTOS reference on first page change the init script to use -interface [ip] and start the service however it still refuses direct connections.

---

### Post by steeldriver on 2016-07-12
What VNC server are you using, and how exactly are you running it?

---

