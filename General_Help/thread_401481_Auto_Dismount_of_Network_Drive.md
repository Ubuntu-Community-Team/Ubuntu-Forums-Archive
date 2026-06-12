---
title: "Auto Dismount of Network Drive"
date: 2007-04-04
forum: General Help
---

### Post by gavinjb on 2007-04-04
Hi,

Does anyone know if it is possible to setup anetwork drive to auto dismount if the server powers off.  

The reason for this is I have a Network Harddisk that I have a backup script that backs up too, the script checks in mtab to see if the drive is mounted before running, but if the drive was available when Linux booted then it will be in mtab.

The entry I have in fstab is

```
//192.168.1.200/Backup /media/Backup cifs umask=000,uid=1000,gid=0,auto,rw,user,
username=user,password=password 0 0
```

Thanks,


Gavin,

---

