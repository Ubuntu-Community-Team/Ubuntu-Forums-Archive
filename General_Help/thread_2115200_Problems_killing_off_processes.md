---
title: "Problems killing off processes"
date: 2013-02-12
forum: General Help
---

### Post by mikeyw on 2013-02-12
Hi, I have two orphaned processes that i'm unable to kill

0 D 1000     10085     1  0  80   0 -  3380 nfs_wa 12:05 ?        00:00:05 cp /confbck/srvcTue.bck /bck/
0 D root     10164     1  0  80   0 -  3122 nfs_wa 12:11 ?        00:00:00 cp /confbck/srvcTue.bck /bck/

They are copying to an NFS share that appears to have hung.

I've unshared the NFS export from it's source but can't unmount it on the client 

/$ sudo umount /bck
umount.nfs: /bck: device is busy
umount.nfs: /bck: device is busy

$fuser -c /bck
Cannot stat /bck: Stale NFS file handle
Cannot stat file /proc/10364/fd/3: Stale NFS file handle


How do i restart the NFS service on the client ?

Failing that is there a way to remove these proceses - i really could do with avoiding a reboot if at all possible.

tia
M

---

### Post by rnerwein on 2013-02-12
> **mikeyw said:**
> Hi, I have two orphaned processes that i'm unable to kill

0 D 1000     10085     1  0  80   0 -  3380 nfs_wa 12:05 ?        00:00:05 cp /confbck/srvcTue.bck /bck/
0 D root     10164     1  0  80   0 -  3122 nfs_wa 12:11 ?        00:00:00 cp /confbck/srvcTue.bck /bck/

They are copying to an NFS share that appears to have hung.

I've unshared the NFS export from it's source but can't unmount it on the client 

/$ sudo umount /bck
umount.nfs: /bck: device is busy
umount.nfs: /bck: device is busy

$fuser -c /bck
Cannot stat /bck: Stale NFS file handle
Cannot stat file /proc/10364/fd/3: Stale NFS file handle


How do i restart the NFS service on the client ?

Failing that is there a way to remove these proceses - i really could do with avoiding a reboot if at all possible.

tia
M
hi
in this situation you can't restart your nfs or kill the process. your processes hang around in the kernel-nfs-stack (see the runqueue in your ps -> nfs_wait) and your nfs was hard mounted (this is a must if you write to the nfs-fs). in my experiance - don't use soft-mounted nfs. you can get unexpected results (nfs isn't top to stack). 
your problem is: your nfs-server is down or you get network problems.
ciao

---

### Post by fdrake on 2013-02-12
> **mikeyw said:**
> Hi, I have two orphaned processes that i'm unable to kill

0 D 1000     10085     1  0  80   0 -  3380 nfs_wa 12:05 ?        00:00:05 cp /confbck/srvcTue.bck /bck/
0 D root     10164     1  0  80   0 -  3122 nfs_wa 12:11 ?        00:00:00 cp /confbck/srvcTue.bck /bck/

They are copying to an NFS share that appears to have hung.

I've unshared the NFS export from it's source but can't unmount it on the client 


try killall cp 

> 
/$ sudo umount /bck
umount.nfs: /bck: device is busy
umount.nfs: /bck: device is busy

$fuser -c /bck
Cannot stat /bck: Stale NFS file handle
Cannot stat file /proc/10364/fd/3: Stale NFS file handle

you cannot unmount since cp is running

[/QUOTE]
How do i restart the NFS service on the client ?

[/QUOTE]

```
start <service-name>
or 
/path/of/service/name start
```

---

