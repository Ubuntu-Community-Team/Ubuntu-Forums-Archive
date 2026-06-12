---
title: "It refuses to leave -_-"
date: 2008-05-17
forum: General Help
---

### Post by CraymelCage on 2008-05-17
Hi I have a problem with my trash can. For some reason when I start up my midea disk partition this thing shows up and doesn't want to go away. Can some one help me give it the boot. Pleas and thank you.

---

### Post by ibuclaw on 2008-05-17
Open up a terminal, and type in:
```

cd /media/disk/.Trash*
sudo chown **username** *.rar

```
Replace "username" with your username. Then try removing the Trash.

Regards
Iain

---

### Post by CraymelCage on 2008-05-17
It doesn't work. It just continues to tell me that the file and the directory doesn't exist.

```
chown: cannot access `_70.rar': No such file or directory

```

---

### Post by dasunst3r on 2008-05-17
Looking at the path of the file you're trying to get rid of, it appears that the file is on an external media of some sort.  Try plugging in that disk again and then emptying your trash.

---

### Post by CraymelCage on 2008-05-17
The "external media drive" is a partition of my hard drive. I unmounted it just now and it asked me to empty the trash like any other external media drive. It did the trick. Current annoyance gone. Can't wait till the next one.

---

