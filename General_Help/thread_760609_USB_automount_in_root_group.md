---
title: "USB automount in root group"
date: 2008-04-20
forum: General Help
---

### Post by masterperas on 2008-04-20
When i plug in my USB pen drive its gets mounted into the root user group and i cant change it with chown, and even chmod does not change permissions of the group wich are none

this is what i get from an ls -l

```
sapiens@peraspor:/media$ ls -l
total 56
lrwxrwxrwx 1 root    root        6 2007-06-15 21:55 cdrom -> cdrom0
drwxr-xr-x 2 root    root     4096 2007-06-15 21:55 cdrom0
drwxrwxrwx 1 root    root    24576 2008-03-23 21:29 sda1
drwxrwx--- 7 root    plugdev  4096 1970-01-01 01:00 sda2
drwx------ 5 sapiens root    22016 1970-01-01 01:00 VERA PEN

```

if i try to chown it i get 

```
sapiens@peraspor:/media$ sudo chown sapiens:sapiens "VERA PEN"
chown: changing ownership of `VERA PEN': Operation not permitted

```

any ideas ? i need it to automount into the sapiens usergroup, also sapiens is a sudoer

---

### Post by masterperas on 2008-04-21
anyone have any ideas on this? if not can someone direct me to a site that might provide me with answers?

---

