---
title: "editing smb.conf file"
date: 2008-04-08
forum: General Help
---

### Post by sightfire on 2008-04-08
I receive error in the konsole when I try to configure the smb.conf file, also I still can't access kubuntu files thought windows. here are the errors:
Error: "/Var/tmp/kdecache-sky" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-sky" is owned by uid 1000 instead of uid 0.
Error: "/temp/ksocket-sky" is owned by uid 1000 instead of uid 0.

and from windows: " \\kubuntu is not accessible. You might not have permission to use this network resource. Contact the adminstrator of this server to find out if you have access permissions.

The network path was not found".

---

### Post by Rocket2DMn on 2008-04-09
For the file ownership properties, it seems that your username owns them rather than root, so you should run
```
sudo chown root:root /var/tmp/kdecache-sky /tmp/kde-sky /temp/ksocket-sky
```
Once you have samba configured correctly, you should have more luck accessing it from windows.

---

