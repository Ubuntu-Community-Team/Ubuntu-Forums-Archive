---
title: "Can't browse DVD+RW made with Leopard"
date: 2008-02-24
forum: General Help
---

### Post by Thermo1 on 2008-02-24
I've got a DVD+RW backup disk which was burnt using Mac OS X Leopard.  When I pop it into my u7.10 machine, the drive mounts on the desktop as expected but when I try to read the folders within, they are all labeled with a padlock and I get an error dialog saying I don't have permissions.

Any ideas where to go from here?

---

### Post by bollix47 on 2008-02-24
Try running nautilus with superuser.

Alt-F2

```
gksudo nautilus
```

If you copy any file from the DVD to your hard drive the permissions may have to be changed using the "sudo chown" command in a terminal.  You can see the options for this command by typing "man chown" (without the quotes) in a terminal.

---

### Post by Thermo1 on 2008-02-24
Thanks, that works great but is there anyway I can do it without having to gksudo?

---

