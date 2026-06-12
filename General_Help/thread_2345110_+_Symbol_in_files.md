---
title: "+ Symbol in files"
date: 2016-11-30
forum: General Help
---

### Post by charles6 on 2016-11-30
Hi,

When I modify my files using Samba (Windows PC), the file extension in Ubuntu adds a "+" symbol at the end of the file.  
Anybody knows how to stop that from happening when I edit my files?  I already have the create mask = 0755 in my smb.conf configuration.

Example:
-rw-rw-r--+

---

### Post by Keith_Helms on 2016-12-01
That indicates that something called an Access Control List (ACL) is  present.  An ACL is extended file permissions and, my impression is,  allows Unix file permissions to more closely resemble Windows file  permissions.

There is probably an option in smb.conf somewhere to  turn them off.  You can also turn them off at the mount level by adding  noacl as a mount option for the permission.  Maybe someone more  familiar with samba could speak to whether disabling them is a good  idea, bad idea, or doesn't matter.

---

