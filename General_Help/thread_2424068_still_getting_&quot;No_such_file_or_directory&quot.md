---
title: "still getting &quot;No such file or directory&quot; from ls"
date: 2019-08-02
forum: General Help
---

### Post by Skaperen on 2019-08-02
i am still getting the error "_No such file or directory_" from the **[FONT=courier new]ls[/FONT]** command for some symlinks.  i have tracked this down to a **[FONT=courier new]lgetxattr()[/FONT]** syscall **[FONT=courier new]ls[/FONT]** is doing that gets a _ENOENT_ error even though the symlink exists.  i suspect it *should* be getting a _ENOATTR_ error, instead. _does anyone know about this and why it has been going on for a long time (at least a year)_?

---

