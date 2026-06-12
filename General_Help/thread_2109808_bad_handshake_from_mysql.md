---
title: "bad handshake from mysql"
date: 2013-01-28
forum: General Help
---

### Post by adrianp918 on 2013-01-28
i am trying to connect to mysql server and i get bad handshake, it is a fresh install of ubuntu with updats applied, any help would be appreciated

---

### Post by adam.stokes on 2013-01-28
Version of mysql, Ubuntu, and any logs or error messages printed to stdout would be helpful.

Also found this during a quick search
[https://bugs.launchpad.net/maria/+bug/982664](https://bugs.launchpad.net/maria/+bug/982664)

---

### Post by adrianp918 on 2013-01-28
Version: 5.5.29-0ubuntu0.12.04.1
Version: 5.5.22-0ubuntu1


and when i just try to connect a email scanner and it says #08S01 Bad Handshake 

there are no logs at all when this happens

---

### Post by adam.stokes on 2013-01-28
```
mysql> status
--------------
mysql  Ver 14.14 Distrib 5.5.29, for debian-linux-gnu (x86_64) using readline 6.2

Connection id:          41
Current database:
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.5.29-0ubuntu0.12.04.1 (Ubuntu)
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    utf8
Conn.  characterset:    utf8
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 32 sec

Threads: 1  Questions: 575  Slow queries: 0  Opens: 421  Flush tables: 1  Open tables: 41  Queries per second avg: 17.968
--------------

```

I am not seeing any issues, are you able to do something simple like:

```
$ mysql -uroot -p<password>
```

Could be something application specific, and since I don't know the details of what application you are using it'd be hard to guess.

---

### Post by adrianp918 on 2013-01-28
when i check the status this is the output 


mysql> status
--------------
mysql  Ver 14.14 Distrib 5.5.29, for debian-linux-gnu (i686) using readline 6.2

Connection id:          46
Current database:
Current user:           root@localhost
SSL:                    Not in use
Current pager:          stdout
Using outfile:          ''
Using delimiter:        ;
Server version:         5.5.29-0ubuntu0.12.04.1 (Ubuntu)
Protocol version:       10
Connection:             Localhost via UNIX socket
Server characterset:    latin1
Db     characterset:    latin1
Client characterset:    utf8
Conn.  characterset:    utf8
UNIX socket:            /var/run/mysqld/mysqld.sock
Uptime:                 22 hours 41 min 59 sec

Threads: 1  Questions: 126  Slow queries: 0  Opens: 171  Flush tables: 1  Open tables: 41  Queries per second avg: 0.001
--------------

---

### Post by adrianp918 on 2013-01-28
i am using a program called Paranoid, i have done a google search with the  number i was given from paranoid and it seems to be a mysql issue.

i have been able to duplicate the same problem on windows and *nix also, and same error,

---

### Post by adrianp918 on 2013-01-28
ok did some research and found out it is a bug with mydac in mysql and they are saying to either upgrade to 5.6.12 or down grade from 5.5 i want to downgrade to last stable version, any idea how to do that

---

### Post by adam.stokes on 2013-01-29
You could visit this question on askubuntu.com that should cover downgrading to a particular version

[http://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get](http://askubuntu.com/questions/138284/how-to-downgrade-a-package-via-apt-get)

---

