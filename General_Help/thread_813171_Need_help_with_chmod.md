---
title: "Need help with chmod"
date: 2008-05-30
forum: General Help
---

### Post by rehat on 2008-05-30
hi I'm new with using Linux and I need help understanding how to manage user accounts with chmod.  I would like to learn how to manage these account through comandline.  What I am trying to do is limit one user account from accessing a folder in my root directory but still be able to access it with my main user account.

example:
with /media I would like to have access to it but prevent another account from opening it.  Basically I would like to prevent a user account from accessing my mounted WXP drives :-) I got my home directory to work this way with drwx------ but when I do this to any directory in root only the root user can access it.  So do I need to do something with groups or other(still don't know that other is for)?  Any help would be great or even a link to a site that has a good explanation on how to do this.

---

### Post by pointone on 2008-05-30
```
$ ls /media/ -l
total 4.0K
lrwxrwxrwx 1 root 999    6 2008-05-08 00:58 cdrom -> cdrom0
drwxr-xr-x 2 root 999 4.0K 2008-05-08 00:58 cdrom0
```

A general example: the "owner" of cdrom0 is root, the "group" is 999. 

"other" refers to users other than root and not in group 999, in this case.

To prevent users from stepping into a directory (i.e., "cd /path/to/dir"), you need to remove the execute bit for "other". 

To prevent users from reading files in a directory (i.e., "ls /path/to/dir"), you need to remove the read bit for "other".

What it sounds like you want to do is:

```
sudo chown root:admin /media
sudo chmod 770 /media
```

...to grant full read/write access to root and members of the "admin" group.

[http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

### Post by rehat on 2008-05-30
sweet thanks that helped

---

### Post by rehat on 2008-05-30
one other question about accessing mounted drives.  Am I fine with restricting access to the /media directory where the mounted drives appear or are there other ways to access them?

---

