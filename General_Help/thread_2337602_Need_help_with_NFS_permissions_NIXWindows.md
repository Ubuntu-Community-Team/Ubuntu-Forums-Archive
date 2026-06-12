---
title: "Need help with NFS permissions NIX/Windows"
date: 2016-09-20
forum: General Help
---

### Post by midknight2 on 2016-09-20
Hoping someone could help me here, I'm running out of ideas from searching around and cant find anything to fix this issue..

set;

Windows 2012 file server.
Ubuntu running under VM (on the 2012)

I have set up the NFS shares on windows. and mounting them as follows

192.168.2.26:/share /mnt/share nfs rsize=8192,wsize=8192,timeo=14,intr

now this works fine, but the problem is as follows.....

if a dir is made under windows it inherits its parents security settings (for testing I made is "Everyone")

now we make a dir though NIX, and its security settings on that dir are different to windows, and now what happens, is if a user on the network tries to browse that dir, they will get permission denied, because the security settings have a random account number, and possibly will continue with administrator and system account from windows..

does anyone know why this is happening and how I can get around it?

---

### Post by TheFu on 2016-09-20
Windows users and Unix users don't use the same uid, so a mapping file is required. usernames mean NOTHING in Windows.  Windows should handle this. Look for their mapping solution.
Please clarify that Windows is running nfsd and that Linux is the client, correct?

Don't use Windows anymore, so can't help farther.

---

### Post by midknight2 on 2016-09-22
i finally found the solution to my problem. by default windows doesn't keep Inheritance on folders made by another system on NFS. be enabling this in the registry it will keep the ACL's, which is exactly what I needed

---

