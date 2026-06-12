---
title: "change password?"
date: 2008-05-16
forum: General Help
---

### Post by tubunu on 2008-05-16
Is it possible to change system wide (user's) password to something else? I don't want to reinstall Ubuntu in order to do that.

---

### Post by Mr A Mouse on 2008-05-16
If you have admin access, you can go to Administration > Users and change password(s) from there.

---

### Post by rlcomstock3 on 2008-05-16
$ passwd username  # changes username
$ passwd           # changes root

$ man passwd       # info on passwd

For more info!

---

### Post by tubunu on 2008-05-19
Thanks! :)

---

### Post by _sAm_ on 2008-05-19
I have done this and got problems. passwd username will not change the username/password for all services running on Ubuntu, like cups and the keyring manager - and I don't know how to do that.

---

