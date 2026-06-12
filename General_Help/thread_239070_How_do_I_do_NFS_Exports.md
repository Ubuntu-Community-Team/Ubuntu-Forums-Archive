---
title: "How do I do NFS Exports????"
date: 2006-08-18
forum: General Help
---

### Post by .t. on 2006-08-18
I've just set up an Ubuntu server, and got Apache how I want. I installed NFS, and am now trying to export my /var/www directory to my local network, so I can do my coding not on an SSH terminal. Here is the exports file:```
# /etc/exports: the access control list for filesystems which may be exported
#               to NFS clients.  See exports(5).
/home/Shared    82.70.109.16/255.255.255.248(rw,sync)
/var/www        82.70.109.16/255.255.255.248(rw,sync)
```and my relevant fstab entries on the client:```
cheetah:/home/Shared /home/Shared nfs   rw,hard         0       0
cheetah:/var/www        /var/www  nfs   rw,hard         0       0
```
The weird thing is is that I can access /home/Shared with rw access, but not /var/www. Is it something to do with the permissions? I'll list them below. What should they be?```
drwxrwxrwx 8 root root    208 2006-08-18 21:38 /home/Shared
drwxr-xr-x  3 root root   80 2006-08-18 16:45 /var/www
```

---

### Post by lamego on 2006-08-18
Firs you should have chosen a better topic, as you already guessed your problem has nothing to do with NFS, its a plain unix/linux permissions question.

Your 
/var/www/apache2-default/ is -rw-r--r-- which means it can only be written by the owner (root).

The solution is to change the owner to the user accessing the file or change the privileges giving write permission to the group and changing the group.

You could also use samba instead of NFS, it is safer ant easier to use for windows compability.

---

### Post by .t. on 2006-08-19
Don't have Windows - don't wanna samba. Thanks for the info - but I'm only trying to access it with root (or does it have to be the local root?).

EDIT: It's all right - I just made /var/www world-writable.

---

