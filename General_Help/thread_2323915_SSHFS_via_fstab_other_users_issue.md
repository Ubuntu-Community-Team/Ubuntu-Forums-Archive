---
title: "SSHFS via fstab other users issue"
date: 2016-05-09
forum: General Help
---

### Post by Berduchwal on 2016-05-09
Running Ubuntu Server 16.04 which hosts the hard drive.

Client running 16.04 connects using following fstab entry:
```
dserver@192.168.1.15:/home/dserver/directory /media/Placement fuse.sshfs _netdev,auto,delay_connect,noatime,allow_other,IdentityFile=/home/localuser/.ssh/id_rsa,idmap=user,gid=1003 0 0
```

It worked before new system (15.10) reinstall. 

Now it works for the localuser who is an administrator (sudoer) but not for any other users. So unless localuser logs in first the other users get input/output error when they try to access the drive. If localuser logs in first and then logs off it works for everyone else.

---

