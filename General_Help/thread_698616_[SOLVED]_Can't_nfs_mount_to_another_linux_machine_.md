---
title: "[SOLVED] Can't nfs mount to another linux machine read-write"
date: 2008-02-16
forum: General Help
---

### Post by Chas_E_Erath on 2008-02-16
Shoot.  This is frustrating. 

I've exported a directory from the upstairs 'server' (hobs)
I can mount.nfs the directory from the downstairs 'client' (skunk) and read everything just fine.

But I can *not* write to the mounted directory from the client (skunk).  Why?


Here's what I've done:

On the server side, I export the directory  '/nfs_test'  read-write

```


root@hobs ~ # cat /etc/exports 
/nfs_test skunk (rw)
root@hobs ~ # 
```

On the client side (skunk) I mount the file system (either through /etc/fstab or with mount.nfs)


```


mount.nfs hobs:/nfs_dir  /hobs/nfs_dir -w
```


I check to make sure its mounted, and that its mounted read-write:


```


root@skunk:~# cat /etc/mtab
/dev/sdb1 / ext3 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
hobs:/nfs_dir /hobs/nfs_dir  nfs rw,addr=192.168.2.2 0 0
root@skunk:~# 
```

I see that in fact it is mounted, and that it is shown as being mounted read-write, but despite that, I can't write to it.


```


root@skunk:~# touch /hobs/nfs_dir/test
touch: cannot touch `/hobs/nfs_dir/test': Read-only file system
root@skunk:~# 
```


I have a feeling I'm missing a silly little flag, or some such.  Can anybody help me?

Thanks very, very much.
Chas.

---

### Post by Chas_E_Erath on 2008-02-16
I'm not sure why that happened, but it seems to have resolved itself somehow during a reboot.

So, uh...nevermind.

---

