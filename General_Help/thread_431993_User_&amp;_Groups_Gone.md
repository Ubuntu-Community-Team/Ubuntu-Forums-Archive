---
title: "User &amp; Groups Gone"
date: 2007-05-03
forum: General Help
---

### Post by Marcelstrijen on 2007-05-03
This morning I had a  user /group option under my system -> Manage tool bar. Now it dissapeared. In the meanwhile I changed my accountname. Maybee this also changed some permissions? I also miss some other options, like adding software. Can someone help me with this problem?

---

### Post by drpaul on 2007-05-03
If you look at the permissions for your current user, you'll probably find that they are missing a bunch compared to your first, original user. If you login with that first user and use sudo you can add the necessary group memberships to your new user.

HTH

Paul

---

### Post by Marcelstrijen on 2007-05-04
The problem is that my oem user, the user which was created during the installation, was renamed. The only user with all rights is my root user, but I don't know how to give the needed groupermissions in the console.

---

### Post by bapoumba on 2007-05-04
Boot in recovery mode. Youl' be root with a **# **prompt, then:
```
# adduser <your_login_here> admin
# reboot
```

here are the groups a standard user with admin privileges is in :
```
:~$ groups
bapoumba adm dialout cdrom floppy audio dip video plugdev netdev lpadmin powerdev scanner admin
```
(bapoumba is my login).
Once in admin group, you can use sudo and add yourself to these standard groups.

---

