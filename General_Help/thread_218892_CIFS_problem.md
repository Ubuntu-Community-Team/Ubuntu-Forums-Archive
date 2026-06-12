---
title: "CIFS problem"
date: 2006-07-19
forum: General Help
---

### Post by macoute on 2006-07-19
I have a LTSP configuration and I'd like to give clients access to my shared folders in W2003 server.
I manage to mount the folders, I can see the contents of it, but there is one big problem.
If I use Open Office to save, it says something like "General I/O error", and can't save. 

My /etc/fstab:
```
//192.168.1.5/oppilaat /home/oppilaat cifs auto,user,credentials=/root/.smbcredentials,umask=0222,rw 0 0
//192.168.1.5/SNO /home/SNO cifs user,credentials=/root/.smbcredentials,umask=000 0 0

```

I have tried changing the umask, but it wont help. That is why they are different.

---

