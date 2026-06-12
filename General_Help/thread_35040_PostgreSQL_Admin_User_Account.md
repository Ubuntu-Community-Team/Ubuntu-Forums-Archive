---
title: "PostgreSQL Admin User Account"
date: 2005-05-17
forum: General Help
---

### Post by gdeswardt on 2005-05-17
So I have installed PostgreSQL via apt-get and know that it is running on my machine. I have also installed pgAdminIII. 

What is the default admin username and password for login on to the postgresql server?

---

### Post by Juergen on 2005-05-17
AFAIR it's postgres and the password is locked just like root's.
You can change to it with
```
sudo su postgres
```but the first thing you should do is to create a database-user with CREATE DATABASE/USER permissions and use that from then on.
On a single-user machine you could probably just use your normal account for this.

---

