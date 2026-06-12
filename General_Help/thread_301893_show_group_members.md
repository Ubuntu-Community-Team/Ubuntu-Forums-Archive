---
title: "show group members"
date: 2006-11-17
forum: General Help
---

### Post by grough on 2006-11-17
I have a collection of files that are read-only (744), but that I am able to write to and delete even though I'm not the owner. What could be the reason for this?

I'm not sure if I'm part of the same group as the owner, even though, as i understand it, having the permissions set to 744 shouldn't allow anybody but the owner to write to the files.

Trying to diagnose my problem, I became stumped by something else: is there a way to the list all groups on a system, or list users that belong to a particular group?

Thanks,
Gavin

---

### Post by taurus on 2006-11-17
```
id
cat /etc/group
```

---

