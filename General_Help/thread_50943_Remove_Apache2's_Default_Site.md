---
title: "Remove Apache2's Default Site"
date: 2005-07-21
forum: General Help
---

### Post by douceur on 2005-07-21
I've just setup apache2 on one of my Ubuntu boxes.  I'm trying to work with virtual hosts, but I'm running into a behavior I'm not quite looking for.  Basically, everything is working fine except when I reach the box with an undefined hostname.  When I do that, it shows the "default" site, which happens to be the first site I defined.  I would like it to just give an error like you would get if you went to alhsdlfkhasf.com, since it doesn't exist.  Is there a way to change this?

---

### Post by Lunde on 2005-07-22
One option is to change the "document root" under httpd.conf

---

