---
title: "Can't install gimp on ubuntu 14.04"
date: 2014-06-26
forum: General Help
---

### Post by jjclonker on 2014-06-26
I get this error after downloading part of gimp via software center:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/w/webkitgtk/libjavascriptcoregtk-1.0-0_2.4.2-1ubuntu0.1_i386.deb 404  Not Found [IP: 91.189.91.13 80]
```

My Internet is fine.
Other downloads are working fine with software center, just not gimp.

---

### Post by nerdtron on 2014-06-26
Try it on the terminal?

sudo apt-get update && sudo apt-get install gimp

Post the complete output here.

---

### Post by jjclonker on 2014-06-26
Thanks, nerdtron. I solved my own problem... I needed to update my computer.

Gimp did not voice any software dependencies, but after I updated overnight it seems to be working just fine.

Solved.:KS

---

