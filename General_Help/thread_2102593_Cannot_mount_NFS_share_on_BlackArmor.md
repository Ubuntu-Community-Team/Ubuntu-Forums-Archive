---
title: "Cannot mount NFS share on BlackArmor"
date: 2013-01-07
forum: General Help
---

### Post by maxxer on 2013-01-07
Hi.
I'm trying to mount an old Seagate BlackArmor using NFS.
I have a Debian 5 system correctly mounting the share, but on my newly installed Ubuntu 10.04 I cannot.

if I run
showmount -e 192.168.1.179
I get
clnt_create rpc program not registered

if I try to directly mount the share using the same command working on debian I get
mount.nfs: an incorrect mount option was specified

Package nfs-common is installed, portmap is running, what else could be wrong?
thanks

---

### Post by onyxtacular on 2013-06-11
I'm working through the same problem.  

I check segate and found this - [http://knowledge.seagate.com/articles/en_US/FAQ/209203en](http://knowledge.seagate.com/articles/en_US/FAQ/209203en) 

there is supposably a flash tutorial, let me know if you get the tutorial  or share working please.

---

