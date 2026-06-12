---
title: "sudo not attached to first user"
date: 2007-05-13
forum: General Help
---

### Post by cashen on 2007-05-13
I downloaded and installed the desktop v 6.10 today, worked fine - rebooted and now the first user does not have sudo capability - I can not add to the sudoers file since I do not have permissions.  I have searched the forum and not found a similar issue - Any ideas?  I assume I will have to reinstall to get sudo back, but what would cause this problem?
thanks

---

### Post by taurus on 2007-05-13
What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
id
```

---

### Post by cashen on 2007-05-13
uid, gid etc are all 1000 - with the user account name.

I've some Solaris experience and the passwd entry line looks normal.  I can not vi the sudoers file, despite trying multiple things.

---

### Post by taurus on 2007-05-13
First of, you need to belong to group adm and admin to be able to use sudo.  So, look for those two groups from the output of 

```
id
```
And if you want to edit /etc/sudoers, you should use visudo

```
sudo visudo
```

---

### Post by cashen on 2007-05-13
The problem is the authorization process for sudo does not believe my account has permission to use sudo.  The account has been relegated to user status and in the log file there is a "user does not have permission" type entry corresponding to any attempt to use sudo.  Also, the menu system no longer shows many of the administrative functions.

I will reinstall tomorrow -

---

### Post by taurus on 2007-05-13
Why reinstall since all you have to do is to add your username name to groups adm and admin in /etc/group.

Boot into recovery mode from GRUB menu and add your username to those two groups (adm is near the top of the file while admin is near the bottom of the file) and you are all set.

```
nano -B /etc/group
```

---

### Post by cashen on 2007-05-14
Yes of course- thanks!

---

