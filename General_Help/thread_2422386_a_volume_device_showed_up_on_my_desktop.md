---
title: "a volume device showed up on my desktop"
date: 2019-07-06
forum: General Help
---

### Post by Skaperen on 2019-07-06
a volume device showed up on my desktop.  i don't know why, or where it  came from.  i tried to mount it but that fails and it tells me the  volume cannot be found.  does anyone know how to find out more info  about it?

---

### Post by #&amp;thj^% on 2019-07-06
Kind of hard to tell you anything smart to use, but try this to see what is mounted:
```
mount
```
and;
```
cat /proc/self/mounts
```
Also this:
```
gnome-disks
```

---

### Post by Skaperen on 2019-07-07
only the usual stuff was mounted, no more, no less.  and the volume icons disappear when mounted.

gnome-disks:

```

lt2a/root /root 1#  gnome-disks
bash: gnome-disks: command not found
lt2a/root /root 2# 

```

---

