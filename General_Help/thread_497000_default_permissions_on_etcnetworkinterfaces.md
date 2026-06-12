---
title: "default permissions on /etc/network/interfaces"
date: 2007-07-09
forum: General Help
---

### Post by k_22 on 2007-07-09
Can someone supply me with the default permissions for this file?  I tried editing it to set a static IP and now I cannot use the GUI after logging in - i just get a white square in the upper left with no prompt. the console shows the system stuck on starting the NFS daemon.  Thanks.

---

### Post by fredj on 2007-07-09
Boot into the recovery kernel and cd /etc/network. Then use the vi editor on the interfaces file.
You need to be an root user to edit it so use sudo vi intefaces if you need to.

---

### Post by jamvegan on 2007-08-16
I came across this thread while trying to help someone else with the same problem.  Hopefully the issue was resolved long ago, but to answer the question posed here:
> -rw-r----- 1 root admin 32 2007-08-04 19:41 /etc/network/interfaces

---

