---
title: "fstab sshfs not mounting on reboot"
date: 2016-05-10
forum: General Help
---

### Post by Jage_Schiff on 2016-05-10
I have created the following etc/fstab entry:

```
user@10.100.100.100:/home/user/app_files_tmp  /home/user/app_files_tmp  fuse.sshfs  auto,user,_netdev,idmap=user,transform_symlinks,identityfile=/home/user/.ssh/id_rsa,allow_other,default_permissions,uid=1000,gid=1001 0 0

```

This works perfectly if as root I do:

```
mount -a
```

The user (not root) has correct access.  However, it does not take effect automatically on reboot.  I have to manually run mount as root.  Any thoughts as to what I am doing wrong?  I want the remote direcetory to mount automatically on reboot.

Thanks!

---

