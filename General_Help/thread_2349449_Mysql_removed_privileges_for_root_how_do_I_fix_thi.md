---
title: "Mysql removed privileges for root how do I fix this"
date: 2017-01-14
forum: General Help
---

### Post by egandt on 2017-01-14
I was trying to fix another acount and removed privileges from the root user, now I'm stuck as I can not do anything in the DB, I can not afford to reinstall and loss data, how to recover?


Thanks,
ERIC

---

### Post by egandt on 2017-01-14
Solution, ended up being to use the "debian-sys-maint" account to recover as it has rights

The password is in plain text in teh file /etc/mysql/debian.cnf

Personally this seems like a security issue, since the plaintext password is in this file, but it sure made recovery easier.

ERIC

---

### Post by chris354 on 2017-01-14
Its not ideal but its not a security issue when the file permissions / ownership are correct because only mysql, root and sudo users should be able to read it which requires a password. If your password has been compromised then in all honestly the password in that file is probably the least of your worries.

As you have resolved the issue, you should use the thread tools drop down at the top your first post and mark it solved to help others who may have the same issue.

---

