---
title: "Duplicate processes?"
date: 2007-07-20
forum: General Help
---

### Post by mykrob on 2007-07-20
Hey-

Running Kubuntu Feisty. I have a web server and postgresql server running for my Sql-ledger software. I was checking the running processes lately, and for whatever reason, I have two instances of apache2 and two instances of postgres.. Is this normal, and if not, how do i keep two of them from running?

[img]http://img385.imageshack.us/img385/1799/desktop1lv5.jpg[/img]


thanks,
-myk

---

### Post by kidders on 2007-07-21
Hi there,

There's nothing inherently wrong with that ... after all, it seems unreasonable (ie inefficient) to expect Apache, for instance, to do *everything* it needs to with only a single process. This is from one of my boxes, that's been running for a few months...```
$ pidof apache2
16762 11763 4570 30435 30433 30432 29292 29093 29092 29090 29080
```In case there was any doubt, **ps** can show me that they're all related to each other, as I would expect (ie they don't represent 11 independent web servers) ...```
root     29080 /usr/sbin/apache2 -k start -DSSL
www-data 29090  \_ /usr/sbin/apache2 -k start -DSSL
www-data 29092  \_ /usr/sbin/apache2 -k start -DSSL
www-data 29093  \_ /usr/sbin/apache2 -k start -DSSL
www-data 29292  \_ /usr/sbin/apache2 -k start -DSSL
www-data 30432  \_ /usr/sbin/apache2 -k start -DSSL
www-data 30433  \_ /usr/sbin/apache2 -k start -DSSL
www-data 30435  \_ /usr/sbin/apache2 -k start -DSSL
www-data  4570  \_ /usr/sbin/apache2 -k start -DSSL
www-data 11763  \_ /usr/sbin/apache2 -k start -DSSL
www-data 16762  \_ /usr/sbin/apache2 -k start -DSSL
```

---

### Post by mykrob on 2007-07-21
thank you :)

---

### Post by kidders on 2007-07-21
No problem. :-)

---

