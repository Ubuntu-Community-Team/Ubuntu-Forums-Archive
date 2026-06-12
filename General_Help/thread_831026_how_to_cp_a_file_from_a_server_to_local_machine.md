---
title: "how to cp a file from a server to local machine?"
date: 2008-06-16
forum: General Help
---

### Post by peteron on 2008-06-16
Anyone knows how to copy a file (using any commands) from a connected linux server to the local machine with Ubuntu installed? 

Thanks a million.

---

### Post by romain31 on 2008-06-16
Hi, 

I think that it works using scp (needs ssh installed):
scp <user>@<serveur>:/<file_on_serveur> <file_on_local_host>

Romain

---

### Post by mali2297 on 2008-06-16
Use **scp**.

The command should be something like
```

scp peteron@serveraddress:/path/to/file .

```

---

### Post by peteron on 2008-06-16
thanks, it works.

I also tried sftp, which is a better way.

---

