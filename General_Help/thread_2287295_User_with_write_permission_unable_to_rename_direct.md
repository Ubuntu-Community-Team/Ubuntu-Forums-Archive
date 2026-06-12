---
title: "User with write permission unable to rename directory"
date: 2015-07-18
forum: General Help
---

### Post by peter1897 on 2015-07-18
I am trying to rename the directory site1 to site2 which is located in /var/www/:

```
max@ubuntu:/var/www$ ll
total 12
drwxr-xr-x  3 root root 4096 2015-07-18 14:43 ./
drwxr-xr-x 17 root root 4096 2015-07-15 16:37 ../
drwxr-xr-x  5 max  max  4096 2015-07-15 23:02 site1/
```

As you can see user max have permission to write but if i try to rename the directory i get "permission denied" error:

```
max@ubuntu:/var/www$ mv site1 site2
mv: cannot move `site1' to `site2': Permission denied
```

I have to use sudo to rename the directory. 
Why i am getting "permission denied" error when the user max have a write permission on this directory?

---

### Post by Lars Noodén on 2015-07-18
The permissions apply to the contents of a directory but not the directory above it.  You have write permission *in* the directory "site1", but write permission *in* the directory above it belongs only to root at the moment.

---

### Post by peter1897 on 2015-07-18
Thanks.

---

