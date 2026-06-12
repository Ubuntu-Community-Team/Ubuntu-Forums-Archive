---
title: "Dapper, Django 0.96, and MySQLdb 1.2.1 p2"
date: 2007-04-12
forum: General Help
---

### Post by djensen47 on 2007-04-12
So the title is slightly cryptic but should work will for searches. I just spent about 2-4 hours trying to get Django 0.96 running on Dapper Ubuntu 6.06

The problem is that Django 0.96 requires a newer version of MySQLdb than is provided with Dapper. So here is what I did, step by step, to fix this. Assume sudo for everything...
```

$ apt-get remove python-mysqldb
$ apt-get intall gcc
$ apt-get install python-dev
$ apt-get install libmysqlclient15-dev
$ wget http://internap.dl.sourceforge.net/sourceforge/mysql-python/MySQL-python-1.2.1_p2.tar.gz
$ tar xvfz MySQL-python-1.2.1_p2.tar.gz
$ cd MySQL-python-1.2.1_p2
$ python setup.py build
$ python setup.py install

```

That should do it. I hope this helps. I also hope this get's indexed and made searchable in Google so that the next person does't have to spend 4 hours on this like I did.

---

### Post by bbzbryce on 2007-04-19
> **djensen47 said:**
> I also hope this get's indexed and made searchable in Google so that the next person does't have to spend 4 hours on this like I did.

Yup definitely did help, and was indexed by google though my search was pretty specific: ubuntu dapper python mysqldb.

Probably wont be a problem once I upgrade my home server to Feisty, but that wont be for a while.

---

### Post by lolocaust on 2007-09-12
Thanks a lot, you saved me 4 hours :)

Hopefully this won't be a problem by the time Hardy is out, when I'll upgrade my servers.

---

### Post by mlemley on 2008-02-03
Just wanted to thank you for your post, it was fantastic, solved my problem without having to ask :)

---

### Post by NZScottie on 2008-02-11
This was a great help to me thanks!

---

