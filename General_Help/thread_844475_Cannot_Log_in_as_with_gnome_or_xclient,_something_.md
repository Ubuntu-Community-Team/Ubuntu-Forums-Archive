---
title: "Cannot Log in as with gnome or xclient, something about disc space"
date: 2008-06-29
forum: General Help
---

### Post by Lord Xeb on 2008-06-29
A message came up just now and said you have tried for 10 seconds to log in and cannot.,, then something about disc space. But I only have about 6 GB of 60 used...

---

### Post by geirha on 2008-06-29
Hit Ctrl+Alt+F1 and log in at the console, then run ```
df -h
``` Are / or /home full? If so, you'll need to clear up some space. Deleting cached packages often helps. ```
sudo apt-get clean
```

---

### Post by Lord Xeb on 2008-06-29
I can log into failsafe Gnome, but that is it (I can also log into the command based thing aswell). But when I do try to log in as gnome or xclient, it just hangs for about 10 secs, then it just crashes and goes back to log in screen. What you told me didn't even work.

---

### Post by geirha on 2008-06-29
Did you get an error message when you ran ```
df -h
``` in the console/terminal? (what you refer to as "command based thing")

---

### Post by Lord Xeb on 2008-06-29
```
deadlysniper@deadlysnipers-purch:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              53G  6.1G   44G  13% /
varrun                506M  108K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   80K  506M   1% /dev
devshm                506M   24K  506M   1% /dev/shm
lrm                   506M   34M  472M   7% /lib/modules/2.6.22-15-generic/volatile
/dev/scd0             624M  624M     0 100% /media/cdrom0

```

---

### Post by Lord Xeb on 2008-06-30
bump

---

