---
title: "source profile"
date: 2004-10-31
forum: General Help
---

### Post by jcscar on 2004-10-31
Everytime I want to do any java compiling, I have to enter this in my root terminal:
```
root@mashed:/home/jcscar # echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/X11R6/bin
root@mashed:/home/jcscar # cd /etc/
root@mashed:/etc # source profile
root@mashed:/etc # echo $PATH
/opt/java/j2sdk1.4.2_06/bin:/usr/local/bin:/usr/local/sbin:/usr/bin:/usr/sbin:/bin:/sbin:/usr/bin/X11:/usr/games
root@mashed:/etc #
``` 
Is there a way to pake it auto load profile? Or do I need to add my java directory path entry to some other file?

---

### Post by jdong on 2004-10-31
You should use /etc/environment to set such variables.

---

