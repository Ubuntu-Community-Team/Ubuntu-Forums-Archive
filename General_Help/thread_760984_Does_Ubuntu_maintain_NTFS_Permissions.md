---
title: "Does Ubuntu maintain NTFS Permissions"
date: 2008-04-20
forum: General Help
---

### Post by Gregory_NZL on 2008-04-20
I would like to know if Ubuntu maintains NTFS file permissions when dual booting and copying files between windows and Linux partitions?

---

### Post by Rocket2DMn on 2008-04-20
Hello, it seems nobody has an answer for you, so I'll try my best.
If you copy a file TO an ntfs partition, it will probably use whatever permissions are default for ntfs (like world access read/write).  If you move files around, it might maintain permissions by doing a bit for bit copy of the existing file.  I don't think ntfs-3g is very detailed on dealing with ntfs permissions, so it may either just always use defaults, or possibly inherit permissions from the folder you are dealing with.  As far as I've seen there isn't a way to configure ntfs permissions from linux, which is why I would be skeptical of any serious permissions capabilities through ntfs-3g.
If you are connecting through samba, ftp, or ssh it should use the permissions of the user that you are getting access with.  For a dual boot or attached hard drive, I imagine it would be as above.

---

### Post by Gregory_NZL on 2008-04-21
Thanks for your reply. Just wanted a heads up :D I will check it out once 8.04 is released

---

### Post by bingoUV on 2008-04-21
Permissions on NTFS are ACLs which depend on the users, groups etc. Those users and groups certainly do not exist in Ubuntu , even if you name the users and groups of Ubuntu exactly as they are in windows. So there is no possibility of the permissions working exactly as in windows.

---

