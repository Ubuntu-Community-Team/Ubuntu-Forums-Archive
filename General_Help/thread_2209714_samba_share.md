---
title: "samba share"
date: 2014-03-07
forum: General Help
---

### Post by Rakesh_vijayan on 2014-03-07
Hi friends 

Today I tried to copy my home from the samba server into the clinet ubuntu desktop ,I follow the command  below in server side 

```
sudo groupadd samba
sudo adduser rakesh samba

sudo visudo

Add a line  in the "group" section :
## Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
%samba   ALL=(ALL) /bin/mount,/bin/umount,/sbin/mount.cifs,/sbin/umount.cifs
```
 
client side 
```
mkdir ~/mnt
sudo mount -t cifs //10.10.10.10/myshare ~/mnt -o username=rakesh,noexec
```

After executing the above command  I got the following message . 

```
root@ns:/home/nadeen# mount -t cifs //10.10.10.10/rakesh /mnt/rakesh/ -o user=rakesh,noexec
Password: 
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)


```

Thanks in Advance for your assistance

---

### Post by TheFu on 2014-03-07
smbtree?

---

