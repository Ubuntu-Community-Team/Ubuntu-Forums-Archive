---
title: "Can 2 different users have the same home directory?"
date: 2007-01-24
forum: General Help
---

### Post by tc101 on 2007-01-24
Can 2 different users have the same home directory?  Could I go into System>Administration>Users and Groups , then select a user, select properties>advanced Tab, and give that user the same home directory as another user? 

 What I am trying to do is give a second, quicker login id and password to myself.

This is ubuntu 6.10

---

### Post by taurus on 2007-01-24
I don't think you can because the second user would have a difference id than the first user.  Then, you will run into all kind of permission problems.

---

### Post by thk on 2007-01-24
There is no reason in principle this cannot be done. Two users can have the same home directory. You would have to carefully set permissions or you could have the users share the same uid.

---

