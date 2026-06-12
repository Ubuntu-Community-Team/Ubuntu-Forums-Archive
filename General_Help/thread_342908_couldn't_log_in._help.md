---
title: "couldn't log in. help"
date: 2007-01-20
forum: General Help
---

### Post by netroy on 2007-01-20
couldn't log in, it said:
gmone-session:4960: libgnonevfs-warning. unable to create /.gnome2 directory: permission denied.

please help, how can i change the permission.

---

### Post by Ecthelion on 2007-01-21
Can you go to a virtual terminal?
You go to one pressing Ctrl-Alt-F1 (F1-F6 works too, F7 brings back the graphical)
Log in.
Go to /home/ and check if you have the permissions to write to your personal dir.
```
cd /home/
ls -l
```

The list you should get should look like this:
> drwxr-xr-x 32      1001      1003 4096 2006-11-26 14:06 computerfair
**drwxr-xr-x** 71 ecthelion ecthelion 8192 2007-01-21 08:53 ecthelion
drwx------  2 root      root      4096 2006-08-18 11:21 lost+found
drwxr-xr-x  2 root      root      4096 2006-11-15 12:05 Recycled
drwxr-xr-x  2      1002      1002 4096 2006-08-04 17:04 sshd

Check if you have  drwxr-xr-x in the line with your username (obviously, where there is "ecthelion" there should be your username :) )

---

