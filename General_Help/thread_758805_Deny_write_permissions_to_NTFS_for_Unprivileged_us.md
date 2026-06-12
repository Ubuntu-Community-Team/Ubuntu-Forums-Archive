---
title: "Deny write permissions to NTFS for Unprivileged users"
date: 2008-04-18
forum: General Help
---

### Post by ibuclaw on 2008-04-18
Hi all.

I'm trying **not** to get write privileges for certain users in Ubuntu.

I've set the fstab line to this:
```
 UUID=6AB0419AB0416E1F /media/.sdb5    ntfs    defaults,umask=002,gid=46 0 1
```

And revoked the users from the group plugdev in /etc/group.

And miraculously they still have write access to the hard-drive.

I've umount, mount the drive and rebooted the system. Before any of you say so.

Any ideas anyone?

Regards
Iain

---

### Post by warp99 on 2008-04-18
Assign the mount point /media/sdb5 to a different user group, then only allow add certain users to that group so all others will be denied write privileges. Example:

Add the group ntfsrw for certain users:
```
sudo addgroup ntfsrw
```
change ownership of the directory:
```
sudo chown root:ntfsrw /media/sda5 
```
and then finally change permissions on the directory:
```
sudo chmod 775 /media/sda5
```
then add your users to the group 'ntfsrw':
```
 sudo addgroup ($user) ntfsrw
``` 
now only root and users of the group ntfsrw have write privileges to the drive.

---

