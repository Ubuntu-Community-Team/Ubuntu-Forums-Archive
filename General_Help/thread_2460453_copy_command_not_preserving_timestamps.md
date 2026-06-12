---
title: "copy command not preserving timestamps"
date: 2021-04-10
forum: General Help
---

### Post by sniper8752 on 2021-04-10
I am trying to copy local files to a remote directory.  I use the "p" flag, but when I view the attributes of the newly copied over files, they all have today's date and time.  Is there something else I need to do to preserve this attribute?

---

### Post by TheFu on 2021-04-10
> **sniper8752 said:**
> I am trying to copy local files to a remote directory.  I use the "p" flag, but when I view the attributes of the newly copied over files, they all have today's date and time.  Is there something else I need to do to preserve this attribute?

What do you mean by "remote directory"?  cifs, NFS, p9?    Something else?  Usually the remote server controls persons, owner, group, acls, xattr and other file properties.

---

### Post by sniper8752 on 2021-04-11
I have a remote cifs share mounted.  I use the cp command to copy a file locally to that locally remote mounted folder.  Hopefully that makes sense.

---

### Post by TheFu on 2021-04-11
Google says to use:
```
mount -t cifs ...
```
not any other method.  Seems the way the storage is mounted matters. 

I tested using cifs v2.1 from ubuntu to Windows and the timestamp was retained with cp -p.

---

