---
title: "Beryl Problem?"
date: 2007-01-11
forum: General Help
---

### Post by Rackerz on 2007-01-11
The title bar is missing, where has it gone?

---

### Post by cmost on 2007-01-11
Are you running the latest Beryl?  (Especially the SVN versions)  Emerald is quite buggy with this version.  Downgrade Emerald to 1571 build and you won't have any problems.

---

### Post by Waappu on 2007-01-11
Hi

See if this helps
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

also adding this to /etc/X11/xorg.conf file Section "Device" might help 
```
Option      	"AGPSize" "32"
```

---

### Post by Rackerz on 2007-01-11
> **Waappu said:**
> Hi

See if this helps
[http://forum.beryl-project.org/viewtopic.php?f=35&t=1500](http://forum.beryl-project.org/viewtopic.php?f=35&t=1500)

also adding this to /etc/X11/xorg.conf file Section "Device" might help 
```
Option      	"AGPSize" "32"
```

Thanks, that seems to have worked :D.

---

### Post by Rackerz on 2007-01-11
Ok now I've got another problem. Before when I used it minimizing windows and such gave out special effects, now it just minimizes normally. Do I need to set anything or has that option killed the effects?

---

### Post by Waappu on 2007-01-11
Hi

Thats wierd. If you remove that line does effect come back ?

---

### Post by oellegaard on 2007-01-11
#4

I have the same problem, but this didn't fix it
Im also runnning Nvidia (Geforce 4) though.

---

