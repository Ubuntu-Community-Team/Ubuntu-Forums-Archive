---
title: "MYSQL - root an error saying Access denied for user 'root'@'localhost' (using passwor"
date: 2008-05-11
forum: General Help
---

### Post by fieldway on 2008-05-11
Just install LAMP, all went fine expect for one thing in mysql
When I ran the command mysql -u  the following message appear (root an error saying Access denied for user 'root'@'localhost' (using password: NO))
I stop mysql and try sudo /usr/bin/mysql –skip-grant-tables—user=root  It came back with unknown variable 'skip-grant-tables—user=root.
Any ideas how to fix this wee issue?

I'm using Ubuntu 8.04 the Hardy Heron

---

### Post by Monicker on 2008-05-11
Were you not prompted to supply the root password during the install?  You should have been.

Even if the password is blank, you have to use the -p option with mysql.

```
mysql -u root -p
```

Then simply hit enter when prompted for the password.

---

