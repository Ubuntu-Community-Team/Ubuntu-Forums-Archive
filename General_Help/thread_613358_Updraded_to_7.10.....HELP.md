---
title: "Updraded to 7.10.....HELP"
date: 2007-11-14
forum: General Help
---

### Post by diirka on 2007-11-14
Ok so I just upgraded to ubuntu 7.10 and no when I restart it gets past the ubuntu loading screen and then just goes black.  Any ideas?  thanks

---

### Post by Tyke91 on 2007-11-14
can you boot into recovery mode? If so then it's a problem with Xserver


if you can get into a recovery console, use this command
```
**dpkg-reconfigure xserver-xorg** 
```

to help reconfigure xserver

---

