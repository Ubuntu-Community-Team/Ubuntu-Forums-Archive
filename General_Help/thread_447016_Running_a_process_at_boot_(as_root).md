---
title: "Running a process at boot (as root)"
date: 2007-05-17
forum: General Help
---

### Post by Yarias on 2007-05-17
I know there is a way to do this, but I'm just unsure how.

Right now, every time I boot, I have to run 'sudo g15daemon' at a terminal in order for my keyboard to be fully supported.

I'm just wondering what the proper Ubuntu way to get this to run at boot is.

Thanks,

---

### Post by heimo on 2007-05-17
Put the line without sudo to rc.local file before exit 0 line:
```
gksudo gedit /etc/rc.local
```

---

