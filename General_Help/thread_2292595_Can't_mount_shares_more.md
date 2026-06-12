---
title: "Can't mount shares more"
date: 2015-08-29
forum: General Help
---

### Post by Factman on 2015-08-29
Hi,

I have problem with mounting a nfs share, it has worked before newer have problems with it before

I'm using Ubuntu 14.04 Server
Login as root user. 
When mounting a share I am getting this error:
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
mount.nfs: an incorrect mount option was specified
mount.nfs: rpc.statd is not running but is required for remote locking.
mount.nfs: Either use '-o nolock' to keep locks local, or start statd.
mount.nfs: an incorrect mount option was specified

How to solve this problem?

1. RPCbind is running
 root@plexsrv02:/mnt# service rpcbind statusrpcbind start/running, process 6477



FSTAB is not changed as i was before. 
I have tried rebooted the server it is not working. 


 Hope someone can help me? :D

---

### Post by Factman on 2015-08-29
Closed i have solved it. it is working now. :)

---

