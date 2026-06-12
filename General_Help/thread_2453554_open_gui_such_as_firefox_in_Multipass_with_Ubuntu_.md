---
title: "open gui such as firefox in Multipass with Ubuntu 20.04.1 LTS"
date: 2020-11-12
forum: General Help
---

### Post by vickyzwq on 2020-11-12
hi,

is it possible to open gui such as firefox in Multipass shell with Ubuntu 20... environment?
Currently it shows: 
Unable to init server: Could not connect:Connection refused.
Error:cannot open display::0

Thanks in advance.

---

### Post by HermanAB on 2020-11-13
Does multipass work with wayland?  The wayland developers do not consider remoting a display to be a useful feature to them, so the rest of the world has to use Xorg.

---

