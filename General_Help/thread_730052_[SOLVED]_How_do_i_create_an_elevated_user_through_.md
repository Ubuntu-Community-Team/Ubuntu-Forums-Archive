---
title: "[SOLVED] How do i create an elevated user through command prompt?"
date: 2008-03-20
forum: General Help
---

### Post by kdarkentity on 2008-03-20
I know that the adduser command allows you to create a new user but defaultly it doesn't permit administrative rights. I am in a situation where i cant access "users-admin" through an interface so all i need to know is how to add a new user that can administer the system.

Thanks in advance.

---

### Post by PeterJS on 2008-03-20
Try:
```

sudo usermod -a -G admin username

```
The -a flag is for append, and the -G is for a seconday group (a -g would set the primary group).

---

### Post by sisco311 on 2008-03-20
```
sudo usermod -a -G admin *username*
```to add an existing user to the admin group.

---

