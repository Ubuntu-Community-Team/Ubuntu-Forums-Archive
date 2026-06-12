---
title: "rsync error: &quot;IO error encountered -- skipping file deletion&quot;"
date: 2006-11-01
forum: General Help
---

### Post by megamania on 2006-11-01
My desktop has two hard disks, one of which is used to host a full backup of the other one.

I use rsync to create a mirror of my home partition. It has worked flawlessly for months, but now I get this error/warning message:

IO error encountered -- skipping file deletion

This problem started right after a clean install of edgy, but to be honest I don't think that's the cause. I have touched file permissions of my home directory in order to fix another issue, so that's more likely to be the problem.

Here's a few info:

I backup the entire /home partition (all users) to mnt/backup

```

gianfranco@gianfranco-desktop:/$ ls-l
[...cut...]
drwxr-xr-x   6 root root  4096 2006-10-29 17:57 home
[...cut...]

```

```

gianfranco@gianfranco-desktop:/home$ ls -l
totale 56
drwxr-xr-x 41 gianfranco gianfranco  4096 2006-11-01 18:12 gianfranco
drwxr-xr-x 14 guest      guest       4096 2006-10-29 18:04 guest
drwxr-xr-x  2 root       root       49152 2006-07-21 21:03 lost+found

```

```

gianfranco@gianfranco-desktop:/mnt$ ls -l
totale 4
drwxrwxrwx 6 gianfranco gianfranco 4096 2006-10-26 22:34 backup

```
Any suggestions?

---

### Post by megamania on 2006-11-02
Anybody? I've been searching for a solution for a while, but still have no clue...

---

### Post by megamania on 2006-11-04
just one last bump, hoping that somebody jumps in with a solution...

---

### Post by eidauk on 2008-05-20
I guess this answer is better late than never. I added the "--ignore-errors" option, which deleted the files. I don't know what was causing the error in the first place, but at least this option allows the deleting to continue despite the errors. I encountered this problem after upgrading to hardy from gutsy.

---

### Post by abhiroopb on 2008-06-14
Hey I get this error after upgrading from gutsy to hardy...

Added your option thanks!

---

### Post by abhiroopb on 2008-06-14
Figured it out....

In hardy there is a hidden folder in /home/user/ called .gvfs...No idea what it is, but just exclude it from your rsync backup.

---

### Post by greco8523 on 2008-06-20
Sounds like your drive has developed bad sectors, I suggest getting your data off and getting a new hard drive.

---

