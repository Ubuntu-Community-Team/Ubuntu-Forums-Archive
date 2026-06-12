---
title: "Recursive chmod help"
date: 2017-09-10
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2017-09-10
i want to mark all files at 644 but i believe folders need the be a 7 (executable) so you can open them
is there a easy way do that without going through every folder individually from files

---

### Post by steeldriver on 2017-09-10
You can use the symbolic mode X 

```

       The  letters  rwxXst select file mode bits for the affected users: read
       (r), write (w), execute (or search for directories) (x), [B]execute/search
       only  if  the file is a directory or already has execute permission for
       some user (X)[/B]

```

So u=rwX,go=rX would be equivalent to octal mode 644 for files and 755 for directories and existing executables

Alternatively, you could skip the in-command recursion and instead use separate find commands to modify the files and directories separately

```

find path/to/dir -type f -execdir chmod 644 {} +

find path/to/dir -type d -execdir chmod 755 {} +

```

---

### Post by pqwoerituytrueiwoq on 2017-09-13
Thanks

---

