---
title: "ls with chmod"
date: 2007-09-23
forum: General Help
---

### Post by bone2006 on 2007-09-23
I've been searching, but can't find the command.  I thought I used it before, but when I'm changing directories on a server and I do a chmod 755 for instance on a directory and I would like to see the changes I've been typing in ls -la
but I thought there was a command to see the number like 755 on directories and folders?

---

### Post by jamvegan on 2007-09-23
I'm not sure if this is what you mean, but if you want to see the long listing for a directory, rather than its contents, you use the -d option.  For instance:
```
ls -ld /home/bone2006
```

---

### Post by bone2006 on 2007-09-24
I'm not infront of a linux system to try it out, but basically if you typed in chmod 777 on a folder or file, what is the command so you can verify that is the number 777.  
I'm not looking for the permission like u+rwx,g+rx,g-w,o+rx, or something like that, looking for the numbers to verify the permissions.

---

### Post by bulldog060 on 2007-09-24
you could just do `stat' .... and look at the line that says "Access: (0755/drwxr-xr-x) Uid: (1000 / bulldog) Gid: (1000 / bulldog)"

~ron

*Side Note: You could just remember that Read(r) = 4, Write(w) = 2, and Execute(x) = 1 .... so drwxr-xr-x => Directory with perms of 755 ( 4+2+1, 4+1, 4+1 )

---

### Post by bone2006 on 2007-09-27
thanks stat was what I was looking for

---

