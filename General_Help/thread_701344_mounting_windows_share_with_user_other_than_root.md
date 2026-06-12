---
title: "mounting windows share with user other than root"
date: 2008-02-19
forum: General Help
---

### Post by FFighter on 2008-02-19
Hello folks,

I have a windows share in my network that I want to use to make some backups. I have a script (rake script)  that compresses the needed files and then copies these to the windows share. Of course, before this process happens, I need to mount this windows share. 

I actually already did it with success using the following command:

sudo mount -t smbfs -o username=user,password=guestt //hera/Backups /home/marcelo/projetos/backups

This does the job, but mounts the share in /home/marcelo/projetos/backups with root being the owner of backups/*. 

I'd like to mount this share as another user (so that backups/* would have another user as owner).

How could I do that?

Thanks,

Marcelo.

---

### Post by cdenley on 2008-02-19
You can try
```

sudo mount -t smbfs -o uid=1000,username=user,password=guestt //hera/Backups /home/marcelo/projetos/backups

```

---

### Post by FFighter on 2008-02-19
Hi cdenley, thanks for the reply!

> **cdenley said:**
> You can try
```

sudo mount -t smbfs -o uid=1000,username=user,password=guestt //hera/Backups /home/marcelo/projetos/backups

```

What's the "uid=1000" part for?

Thanks again,

Marcelo.

---

### Post by cdenley on 2008-02-19
Every user has a uid (user id). By default, the initial user has 1000 as a uid.

```

man mount.smbfs

```
> 
sets the uid that will own all files on the mounted  filesystem.  It may be specified as either a username or a numeric uid.


---

