---
title: "Question about chmod 3775"
date: 2013-03-20
forum: General Help
---

### Post by crash369 on 2013-03-20
Hello all

I understand about using setgid and sticky bit by running chmod 3775 on directories to make them shareable with members of the same group.
How do I recurse through a shared directory and set those permissions without also changing all the non-directory files to o+x,g+x?

Thanks

---

### Post by bab1 on 2013-03-20
> **crash369 said:**
> Hello all

I understand about using setgid and sticky bit by running chmod 3775 on directories to make them shareable with members of the same group.
How do I recurse through a shared directory and set those permissions without also changing all the non-directory files to o+x,g+x?

Thanks

The sticky bit is NOT for directories with users in the SAME user group.  There isn't any clean way to recurse through a directory tree setting only the directory permissions.  The command chmod will change all permissions (directory and files) using *chmod -R*.

The best way to set this up is to start with a new empty directory and apply the permissions that you want.  What are you attempting to do here?

---

### Post by papibe on 2013-03-20
Hi crash369.

If you want to set different permissions for files and directories, you can't use 'chmod -R'.

I'd recommend using two 'find' commands instead.

For directories:
```
find /path/to/project -type d -exec chmod 3775 '{}' \;
```
and for files:
```
find /path/to/project -type f -exec chmod 0644 '{}' \;
```
Adjust the permissions acording to your needs.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by crash369 on 2013-03-22
Thanks papibe!

Precisely what I was looking for to conver my old shared dir to new perms.

---

