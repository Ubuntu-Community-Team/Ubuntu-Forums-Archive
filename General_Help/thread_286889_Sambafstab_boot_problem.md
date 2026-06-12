---
title: "Samba/fstab boot problem"
date: 2006-10-28
forum: General Help
---

### Post by Dagur on 2006-10-28
I have an old computer with a samba server and I mount 2 directories on it on my working computer. It works great if I mount them manually or if I edit /etc/fstab and do 'mount -a'.
If I reboot, however, it takes a very long time and everything is very slow (unusable really).

This is a problem I had to deal with on dapper. I didn't expect it see it again.

btw, this is how I do it:

```

//192.168.2.200/ftpuser /home/dagur/ftpuser smbfs username=fake,password=pass,uid=1000,gid=1000 0 0 
//192.168.2.200/dagur /home/dagur/server smbfs username=fake,password=pass,uid=1000,gid=1000 0 0

```

---

### Post by krismatth3 on 2006-10-28
I have the exact same problem, mounting the samba shares in the same way.

---

### Post by beerfan on 2006-10-29
Perhaps you already know about this but if you don't need a real mount point (for some script or application that doesn't grok gnomevfs) you can just 'Connect to server' in the places menu and access your samba shares there as needed.

---

### Post by Dagur on 2006-10-30
I need to have this mounted when I boot so it's not quite what I want.

---

### Post by krismatth3 on 2006-10-30
Yes, I want mine always mounted - I never want to have to manually mount the samba share.

---

### Post by Dagur on 2006-11-06
bump :-/


btw, I found the [original bug report](http://www.ubuntuforums.org/showthread.php?p=412516)

---

