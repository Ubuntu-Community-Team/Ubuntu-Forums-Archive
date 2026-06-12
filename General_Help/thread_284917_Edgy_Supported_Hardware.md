---
title: "Edgy Supported Hardware"
date: 2006-10-26
forum: General Help
---

### Post by calvinthomas on 2006-10-26
I haven't seen another thread around like this so if there is I apologise and ask the mods to close this thread but I thought it might be useful to list hardware that people have that they have working in Ubuntu Edgy so people can see easily what works.

My Hardware:

Acer Ferarri 4000 Laptop.

All parts working perfectly except the below:

**Working with some work**

Wireless network with WPA protection (wireless card Broadcom 4318). See How-To Thread for this card.

Graphics card ATI Mobility Radeon X700. Required switching to vesa driver like so:

```
sudo dpkg-reconfigure xserver-xorg
```

and choosing vesa driver, to boot after install or from the live CD and then required installation of ATI driver manually (see the WIKI).

Everything else works perfectly.

Calv

---

### Post by Jussi Kukkonen on 2006-10-26
There's a wiki page in wiki.ubuntu.com with laptop support information (with specific models listed), try there.

---

