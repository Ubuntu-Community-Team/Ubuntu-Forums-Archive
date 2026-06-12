---
title: "Parallel port access as non root user?"
date: 2006-09-21
forum: General Help
---

### Post by edderd on 2006-09-21
I'm trying to access the parallel port (/dev/lp0) from a non root process. 

This seems like a permissions problem, but I can't seem to get around it. 

Basically I have a program that can only access the port if it runs as root.
Here's what happens when I run as root:
root@falcon:~/src/k74- 1.0# ./pprxtx all set
root@falcon:~/src/k74-1.0# ./pprxtx read
255
root@falcon:~/src/k74-1.0# ./pprxtx all clear
root@falcon:~/src/k74-1.0# ./pprxtx read
0

Here's what happens when I run as a non root user (ed):
ed@falcon:~/src/k74-1.0$ ./pprxtx all set
/dev/port: Permission denied
ed@falcon:~/src/k74-1.0$ ./pprxtx read
/dev/port: Permission denied

/dev/lp0 I thought that all I had to do was to add my non rootport  user to the device group (lp) in /etc/group and then that user would have permissions to read and write to that device.
lp:x:7:cupsys, ed

I also changed the device permissions to
  /dev:
  crw-rw-rw- 1 root lp 6, 0 2006-09-21 04:56 lp0

I still can't access the port unless I run as root.

If I change the /dev/port (dangerously insecure) permissions to
  /dev:
  crw-rw-rw- 1 root kmem 1, 4 2006-09-21 04:56 port

I then get:
ed@falcon:~/src/k74-1.0$ ./pprxtx read
/dev/port: Operation not permitted
ed@falcon:~/src/k74-1.0$ ./pprxtx all set
/dev/port: Operation not permitted

Any ideas? I've done a fair amount of googling this and it seems like I'm doing everything correctly.

Thanks,

---

