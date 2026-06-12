---
title: "ubuntu 13.10 nfs failure."
date: 2013-11-09
forum: General Help
---

### Post by odror on 2013-11-09
The problem is simple.
The nfs server is running,

When I try to mount I get 
> mount.nfs: mount system call failed
and the syslog shows
> RPC: AUTH_GSS upcall timed out.
Please check user daemon is running.

What is the user daemon. 
when starting  nfs-kernel-server supposed to take care of everything. Am I missing something.

Is there a way to get more specific debugging info.

Thanks

---

### Post by jasonajensen on 2014-01-08
> **odror said:**
> The problem is simple.
The nfs server is running,

When I try to mount I get 

and the syslog shows


What is the user daemon. 
when starting  nfs-kernel-server supposed to take care of everything. Am I missing something.

Is there a way to get more specific debugging info.

Thanks


I am having the exact same problem...

---

### Post by Zill on 2014-01-08
If you get the following error logged:
```
RPC: AUTH_GSS upcall timed out.
Please check user daemon is running.
```
then edit /etc/default/nfs-common to start gssd daemon ...
```
# Do you want to start the gssd daemon? It is required for Kerberos mounts.
NEED_GSSD=**[COLOR="#FF0000"]yes[/COLOR]**
```
followed by...
```
sudo /etc/init.d/portmap restart
sudo /etc/init.d/nfs-kernel-server restart
sudo /etc/init.d/nfs-common restart
```
Verify rpc.gssd is running with...
```
ps -A |grep rpc
```

---

