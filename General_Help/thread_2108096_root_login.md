---
title: "root login"
date: 2013-01-23
forum: General Help
---

### Post by pinakid on 2013-01-23
Can any body help me, I have installed Ubuntu(x64) 12.04 in a virtual machine(oracle). Now my question is how can I login as 'root' in Ubuntu. Also I have another admin user, I would like both root & 2nd admin users are visible, when Ubuntu boot up.
Thank You,
pinaki

---

### Post by gordintoronto on 2013-01-23
Root login is not available. However, you can execute a command as root (eg. sudo chmod ...) or run a GUI program as root (eg. gksudo nautilus).

---

### Post by sidzen on 2013-01-23
Welcome!

NOTE: don't use a VM

In a terminal, [PHP]sudo useradd -m username
[/PHP] to create user and his home directory
[PHP]sudo passwd username
[/PHP] to create his password

Go to Users and Groups to edit his group and permissions, as well as your own.



Best wishes!

---

### Post by fdrake on 2013-01-23
> **pinakid said:**
> how can I login as 'root' in Ubuntu

```
sudo su
```
or in grub select recovery mode> root shell

>  I would like both root & 2nd admin users are visible, when Ubuntu boot up.

see above posts.

---

