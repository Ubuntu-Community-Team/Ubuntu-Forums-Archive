---
title: "howto reset password in mysql"
date: 2015-01-20
forum: General Help
---

### Post by johnnybgoode on 2015-01-20
after I got access to mysql with the pasword generated via debian.cnf, i would create a new PW. How do I do it?

---

### Post by Holger_Gehrke on 2015-01-20
From a terminal use
```

mysqladmin -u <username> -p password

```
Replace <username> with your MySQL-username. mysqladmin will prompt for your current password, and then ask for the new one twice.

---

### Post by johnnybgoode on 2015-01-21
solved
Thank you

---

