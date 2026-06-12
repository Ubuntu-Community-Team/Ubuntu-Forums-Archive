---
title: "Root owned file ownership changes when copied"
date: 2020-06-21
forum: General Help
---

### Post by raleigh3 on 2020-06-21
When I copy using Thunar, any root owned file to a directory I own, the owner changes to me?

I am trying to test a thunar custom action that changes file ownership.

Thanks.

---

### Post by Dennis N on 2020-06-21
Using cp, that's the way it works without additional options - the new copy has its ownership changed to the user running the cp command.

---

### Post by Impavidus on 2020-06-22
Whenever you copy a file, you create the copy, therefore you own the copy. Which the right options, cp and rsync (and the gui file managers, I presume; I don't use them) can preserve ownership, but only when run by root.

When moving a file within a filesystem or creating a new hardlink, this is different. In that case no new file is created, so ownership is preserved.

---

### Post by raleigh3 on 2020-06-22
```
When moving a file within a filesystem or creating a new hardlink, this is different. In that case no new file is created, so ownership is preserved. 

```
Do you mean copying the file to another root owned directory?

---

### Post by Impavidus on 2020-06-23
> **raleigh3 said:**
> ```
When moving a file within a filesystem or creating a new hardlink, this is different. In that case no new file is created, so ownership is preserved. 

```
Do you mean copying the file to another root owned directory?

No, I mean moving the file to a different directory on the same filesystem or creating a hardlink, exactly as I wrote. In fact, the cp command can create hardlinks if you use the -l option. On first sight, the file will look like a copy, but it will have the owner, group, permissions and access times of the original file (where a copy has those properties from the copy process, which can set some of them to be identical to the original) and if you change the copy, the original will change too. Because it isn't really a copy, but an alternative name to access the same file.

---

### Post by TheFu on 2020-06-23
**The TL;DR version: **
The **owner of the process running the command** doing the copy is the owner of the newly created file/directory.  No way around that, unless root is the owner of that process and the commands support a "retain ownership+permissions" option(s).

The above is always true.

**The longer, more details, probably confusing version:**
By using automation, we can control which userid is the owner of the process - by controlling who runs the copy. There are user crontabs and there are root crontabs.  If the copy is performed using the root crontab AND the command used supports retaining permissions/ownership, then that will happen.  sudo can be used for that, but running most GUI programs via sudo is a terrible idea and can lead to highly undesirable side-effects, including a system that will not allow logins. In short, don't do that.

Hardlinking probably isn't all that useful 99.95% of the time. Where it really becomes useful is for creating versioned backups, though there are some not great limitations with that method. IMHO, there are easier and better ways to make versioned backups.

Both **cp** and **rsync** have options (as spelled out in the manpages for each command) to have a process running under root to retain all owner, group, permissions, ACLs and xattrs as the original file.  Only root can accomplish this. No other userid can.

---

