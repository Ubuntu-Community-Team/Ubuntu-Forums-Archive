---
title: "Permissions with external HD"
date: 2007-05-23
forum: General Help
---

### Post by zheepeez on 2007-05-23
I've got an external HD and a Windows partition and my Ubuntu Studio (which is pretty much the same as normal Ubuntu in terms of basic operating) installation won't let me give myself read-write access to either the Windows partition or the external HD, because "I am not the owner"

How do I get write access to these?

Cheers

---

### Post by booljayj on 2007-05-26
I believe you have to change the permissions as root. I'm not very good at coding, but using this:

```
chmod -R 777 path
```
will modify a folder and its contents so that anyone can read/write/execute them. You would need to use the path that the drive is mounted to, under /media/... or something similar. Look up chmod on Google to get some better information on it.

Consequentially, is your windows drive ntfs? If so, you should know that writing to an ntfs volume is risky, because there is always a chance that the volume could become corrupt and unreadable. That's why ntfs support is still considered unstable. Although, making it a Fat32 volume could make that point moot. I don't know what you've got, though.

---

