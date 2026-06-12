---
title: "Navigating though files..Help"
date: 2007-11-12
forum: General Help
---

### Post by drzero1 on 2007-11-12
```
******@******-computer:~$ ls -al  /home/****/.wine/drive_c/Program Files/
ls: /home/****/.wine/drive_c/Program Files: No such file or directory
ls: Files/: No such file or directory

```

```
******@******-computer:~$ ls -al  /home/******/.wine/drive_c/
total 16
drwxr-xr-x  4 ****** 4096 2007-11-10 14:43 .
drwxr-xr-x  4 ****** 4096 2007-11-12 18:50 ..
drwxr-xr-x  6 ****** 4096 2007-11-10 15:56 Program Files
drwxr-xr-x 12 ****** 4096 2007-11-10 15:23 windows

```

Hmmmm....That makes sense...

I can't get into that folder. Some help would be nice :)

---

### Post by taurus on 2007-11-12
You have to use " " or \ for **Program Files** since there is a space between those two words.

```
ls -al  /home/****/.wine/drive_c/"Program Files"
-or-
ls -al  /home/****/.wine/drive_c/Program\ Files
```

---

### Post by drzero1 on 2007-11-12
Thanks.

---

