---
title: "Database on CD/DVD?"
date: 2008-01-03
forum: General Help
---

### Post by externalsupport on 2008-01-03
Morning all.

I have a MySQL database that does some simple document managment and is searchable from a webpage using PHP. My question is .... Is it possible to transsfer that database to a CD for distribution to customers so that they can search the databse off line? Ideally I would love to transfer the whole lot (webpage etc).

Many thanks 

Ste

---

### Post by kidders on 2008-01-04
Hi there,

Since your users will (obviously) need their own MySQL server, web server & PHP preprocessor to use your database, I would suggest distributing a basic SQL dump with the other files on your disc, to avoid as many snags as possible.

You could do something like ...```
mysqldump -u privileged_user -p dbname | gzip > ~/db.sql.gz

[SIZE=1] ... or if your database needs a *lot* of compression ...
[/SIZE]
mysqldump -u privileged_user -p dbname | bzip2 > ~/db.sql.bz2
```

You would need to package additional SQL with your dump, to create a MySQL user (for your PHP scripts) with enough privileges to access the imported database.

---

