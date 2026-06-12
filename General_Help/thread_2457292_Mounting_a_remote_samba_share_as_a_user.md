---
title: "Mounting a remote samba share as a user"
date: 2021-01-29
forum: General Help
---

### Post by sniper8752 on 2021-01-29
I am trying to mount a remote samba share as a certain local user.  Here is how I am doing it:
```
mount -t smb3 //192.168.0.7/share/ -o rw,credentials=/root/.cifs,username=1000
```
But I get this error:
cannot mount //192.168.0.7/share/ read-only.

---

### Post by TheFu on 2021-01-30
The share is exported read-only for the credentials, not rw.  Try changing the rw option to ro or leave it off completely?

You might want some other options.
```
iocharset=utf8,ro,uid=1000,gid=1000,file_mode=0664,dir_mode=0775
```

The correct uid and gid numbers can be found using the 'id' command, but 1000 for each is very common for a single-user linux client.

But if the server and the client are both Linux/Unix, why not use NFS instead?

---

