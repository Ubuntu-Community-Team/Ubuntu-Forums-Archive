---
title: "Permissions on NTFS drive"
date: 2007-05-13
forum: General Help
---

### Post by mikeize on 2007-05-13
Hi there,

Is there any possible way to change permissions on an NTFS drive?  I have it automatically mounting/ntfs-3g etc, and it works fine (read/write/access/play), but I can't change the owner or any permissions.  Is there some way to do this?  As in, restrict access to certain users, while allowing access to others.

-mike

---

### Post by ariek on 2007-05-13
I think that this privilege is only for the OS controlling the users for that filesystem, ie. only Windows knows those users.

---

### Post by CocoAUS on 2007-05-13
It's an issue with whatever craptastic feature they added in Feisty.  Ever since the new ntfs stuff was added, it's done something to lock the drive down and not allow proper administration.  Not sure what they did.

---

### Post by ariek on 2007-05-13
I think it has to do with the fact that by default all the priviledges are set to 777 (full access) to everyone.

---

### Post by Ergo on 2007-05-13
Sorry to go against you, but that is not the case with me.  In fact, it is the other way around.  No one can access.  The files on that drive can not be accessed till  a password is given.  Real irritating if you need to open something with another program . . . it can't even see the drive the files are on until you try to access it through a browser and answer a password question.

---

### Post by ariek on 2007-05-13
Have you already read this artikel? [https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

