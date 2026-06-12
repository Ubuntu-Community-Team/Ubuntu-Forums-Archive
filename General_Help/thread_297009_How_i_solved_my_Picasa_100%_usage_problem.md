---
title: "How i solved my Picasa 100% usage problem"
date: 2006-11-10
forum: General Help
---

### Post by mjreged on 2006-11-10
I now realize that when you install picasa DEB from google website Wine is also included inside the package, and the provided script that initaites picasa2.exe uses the inluded WINE.. That's bad because i causes my CPU usage 100%

so i went into the picasa folder :
/opt/picasa/wine/drive_c/Program Files/Picasa2

and executed :

wine Picasa2.exe

in this case i am running picasa with WINE that was installed by ubuntu repositories and now my problem is gone. Now Picasa is usuable again

---

### Post by jackmg on 2006-12-24
Just curious. Picasa2 does not make backup copies. It is grayed out. Can you jot down step-by-step how to disable or exclude wine?

Thanks

---

### Post by st14n on 2007-01-01
I found another solution to this problem. Add the following at line 4 of /usr/bin/picasa:
```
export LD_PRELOAD=/usr/lib/libdbus-1.so.3
```
Look at [this page]("http://groups-beta.google.com/group/Google-Labs-Picasa-for-Linux/browse_thread/thread/d06c8f862c07aa57") for more info.

---

