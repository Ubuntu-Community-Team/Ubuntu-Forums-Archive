---
title: "Create new user with root priviliges?"
date: 2006-11-19
forum: General Help
---

### Post by pompiuses on 2006-11-19
How can I create a new user (from the console) which has all the same priviliges as the root user?

---

### Post by aysiu on 2006-11-19
```
sudo adduser *username* admin
``` will allow that user to have root privileges for any command preceded by the word *sudo*.

---

### Post by steve.horsley on 2006-11-19
No other user can have root's priviliges. But if you put the new users in the **admin** group, they will be able to use the sudo command to borrow root privilege in the same way that you do.

---

