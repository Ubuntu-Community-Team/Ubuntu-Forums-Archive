---
title: "Weird Permissions Problem on Directory"
date: 2007-04-03
forum: General Help
---

### Post by aparsons on 2007-04-03
Does anyone know why I wouldn't be able to get into the /data/music directory.  My permissions are set correctly and I obviously have no idea what the problem is....

```
aparsons@apkcfs1:/data$ ls -ltr|grep music
drwxrw-r--  4 rsync    users   96 2006-11-04 11:28 music
aparsons@apkcfs1:/data$ cd music/
-bash: cd: music/: Permission denied
aparsons@apkcfs1:/data$ id
uid=1000(aparsons) gid=1000(aparsons) groups=100(users),1000(aparsons)
aparsons@apkcfs1:/data$ cd ..
aparsons@apkcfs1:/$ ls -ltr|grep data
drwxrwxr-- 12 root users   296 2007-02-28 23:39 data
aparsons@apkcfs1:/$

```

Thanks in advance.

- Allan Parsons

---

### Post by songamericadj on 2007-04-03
try checking in the "users and groups" and see what your permissions are. you might want to try setting your permissions to "sudo" and see if that works. hope it does, hope i helped a little!

---

### Post by aparsons on 2007-04-03
I disabled sudo by issued "sudo passwd root" (sorry, personal preference).  What do you mean by  "checking users and groups."  (p.s. I'm running ubuntu server 6.10).

-Allan Parsons

---

### Post by aparsons on 2007-04-03
I think I figured it out (and it may be a bug).  Apparantly you need execute permissions on directories you want to browse.  So I changed permissions to:

drwxr-xr--  4 rsync    users   96 2006-11-04 11:28 music

from 

drwxr--r--  4 rsync    users   96 2006-11-04 11:28 music

and it worked.  Daily WTF i guess....


- Allan Parsons

---

