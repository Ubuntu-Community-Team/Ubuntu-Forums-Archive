---
title: "Looking for nfs-kernel-server 1:1.2.0-4ubuntu4.1 (10.04 LTS)"
date: 2013-12-16
forum: General Help
---

### Post by benny3 on 2013-12-16
We have an old production NFS server (10.04 LTS) running 2.6.32-22-server, nfs-kernel-server (1:1.2.0-4ubuntu4.1), and nfs-common (1:1.2.0-4ubuntu4.1).  This server is starting to experience what we believe to be issues with the kernel and overall nfsops.  I want to test updating the kernel and nfs packages on a VM prior to doing it on our live server, but unfortunately I can only find 1:1.2.0-4ubuntu4.2 and 1:1.2.0-4ubuntu4.  Does anyone know where I can get the 1:1.2.0-4ubuntu4.1 packages for nfs-common and nfs-kernel-server.  Thank you in advance for any and all help

---

### Post by GraysonPeddie on 2013-12-16
Curious. Have you tried:

```
sudo apt-get install nfs-kernel-server=1:1.2.0-4ubuntu4.1 nfs-common=1:1.2.0-4ubuntu4.1
```

?

Are there any reasons why you don't a newer version of nfs-kernel-server and nfs-common?

---

