---
title: "I cannot find my xorg.conf in Feisty!"
date: 2007-06-17
forum: General Help
---

### Post by Macchi on 2007-06-17
Incredibly embarasing but I cannot find where my xorg.conf in Feisty!

It is not in the good old place, namely /etc/X11/xorg.conf . I have been searching around and cannot find it in the computer.  Is it possible that Beryl or Automatix messed up the installation or "kidnapped" xorg.conf to some other place?

Thanks for any hints.

---

### Post by s.deleeuw on 2007-06-17
Check your logfile:

```
sander@slwork:~$ cat /var/log/Xorg.0.log | grep "xorg.conf"
(==) Using config file: "/etc/X11/xorg.conf"
```

---

### Post by mills on 2007-06-17
have you tried locate?

```
locate xorg.conf
```

---

### Post by bukwirm on 2007-06-17
You could also run "updatedb", then "locate xorg.conf".

---

