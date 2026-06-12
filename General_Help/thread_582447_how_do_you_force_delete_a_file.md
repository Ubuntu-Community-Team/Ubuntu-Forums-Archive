---
title: "how do you force delete a file?"
date: 2007-10-19
forum: General Help
---

### Post by sveznajuci on 2007-10-19
i have a folder that when i put in the trash can wont erase. I get the error ""/home/mahen/....sysinfo.la" cannot be deleted because you do not have permissions to modify its parent folder." How do i delete it? is it possible to do it through terminal?

---

### Post by anubhavrocks on 2007-10-19
From terminal
```
sudo rm path_of_file
```

---

### Post by MR.UNOWEN on 2007-10-28
> What's the force delete command to get rid of directories? That command doesn't seem to get rid of directories


Never mind I found it. (sudo rmdir)

---

### Post by nick_h on 2007-10-28
You need the -r option.  Be careful and consider using it with -i.

---

