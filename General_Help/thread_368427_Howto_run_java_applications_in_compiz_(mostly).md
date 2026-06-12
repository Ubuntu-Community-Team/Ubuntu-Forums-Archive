---
title: "Howto: run java applications in compiz (mostly)"
date: 2007-02-23
forum: General Help
---

### Post by stani on 2007-02-23
Some Java applications give you a blank useless gray window with compiz. The following tip seems to work for many cases, but unfortunately not all. (Tested on Edgy.)

Open a terminal and type:
```
sudo gedit /etc/profile
```

Add this line at the end:
```
export AWT_TOOLKIT=MToolkit
```

---

