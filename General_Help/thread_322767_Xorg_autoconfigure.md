---
title: "Xorg autoconfigure"
date: 2006-12-21
forum: General Help
---

### Post by ejohney on 2006-12-21
Does anyone know how the livecd creates the xorg.conf file?

I'm building a diskless image that will be booted from several different machines and I would like the xorg config file to be automatically configured on boot.  Any ideas on how to accomplish this?

---

### Post by ninotob on 2007-01-13
This would be a nice to know answer because the dpkg-reconfigure xserver-xorg answere given to every issue regarding X sure as heck doesn't do the same thing.  (sorry, the usual X frustration is getting to me)

---

### Post by tagra123 on 2007-01-20
Anyone?

---

### Post by ~LoKe on 2007-01-20
> **ninotob said:**
> This would be a nice to know answer because the dpkg-reconfigure xserver-xorg answere given to every issue regarding X sure as heck doesn't do the same thing.  (sorry, the usual X frustration is getting to me)

How do you figure?
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Would automatically configure it based on the system in question.  Always worked for me.

---

