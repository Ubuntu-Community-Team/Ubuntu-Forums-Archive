---
title: "print permission to user"
date: 2008-01-12
forum: General Help
---

### Post by atheistkun on 2008-01-12
I wish to create a user which can only do ssh login and then print. I created one and removed all the permission given in 'permission tab' since none of it related to print. But then later found user cannot print using lpr. 

How should I give the user permission?

---

### Post by Rocket2DMn on 2008-01-12
User should have "read' permission on the file(s).  If you assign a particular group to the file(s) you want the user to access, then put that user in that group, you can specify Group permissions on the file(s) to be read/printed.  This way the file owner still has their original permissions.

---

### Post by atheistkun on 2008-01-13
The created user has all the permission on file but not to 'print' any file. I mean 'print' privileges.

---

### Post by Rocket2DMn on 2008-01-13
There is no specific "print" permission.  If a user can read a file, then they can use their text editor (or other program) to print the contents of the file.  The permissions in *nix are Read, Write, and Execute and they can be assigned according to User, Group, and World.

---

