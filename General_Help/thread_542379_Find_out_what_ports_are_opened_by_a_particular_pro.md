---
title: "Find out what ports are opened by a particular process"
date: 2007-09-03
forum: General Help
---

### Post by yinglcs2 on 2007-09-03
Hi,

From this article, I am able to find out what file descriptor are opened by a particular process.

And the /proc/<prorcess id>/fd shows:

lrwx------ 1 root root 64 2007-09-03 20:58 14 -> socket:[25470]
lrwx------ 1 root root 64 2007-09-03 20:58 15 -> socket:[25471]
lrwx------ 1 root root 64 2007-09-03 20:58 16 -> socket:[25472]
lrwx------ 1 root root 64 2007-09-03 20:58 17 -> socket:[25473]
lrwx------ 1 root root 64 2007-09-03 20:58 18 -> socket:[25474]
lrwx------ 1 root root 64 2007-09-03 20:58 19 -> socket:[25475]


How can i find out what are the ports associated with each socket  in the ' /proc/<prorcess id>/fd' file?

[http://www.cyberciti.biz/tips/linux-procfs-file-descriptors.html](http://www.cyberciti.biz/tips/linux-procfs-file-descriptors.html)

---

### Post by jamvegan on 2007-09-04
```
sudo lsof -i
```
This might be what you're looking for.  It seems to only explicitly list the port when it is non-standard.  If you need to know the port for one of the processes that does not explicitly show it, you can look up the name in /etc/services.  For instance:
```
grep mdns /etc/services
```

---

### Post by cwaldbieser on 2007-09-05
```

$ netstat -tcp -p

```
You can grep for the process ID you want.

---

