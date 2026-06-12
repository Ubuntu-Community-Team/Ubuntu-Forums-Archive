---
title: "phppgadmin: login failed"
date: 2008-06-11
forum: General Help
---

### Post by fozzyuw on 2008-06-11
Hi all,

I've found several websites and Ubuntu forum threads on this topic but so far (after 2 days of tring) I've not managed to figure out why phpPgAdmin isn't working.

Here's the facts.

postgreSql 8.3 -> installed and working fine, I can log via the CLI
Apache2 -> Installed and working fine
PHP5  -> Installed and working (presumably) fine.  I can write PHP scripts and I have Zend Framework working fine.

Now, for phpPgAdmin.

* I did **not** install it via "sudo apt-get install phppgadmin".  I downloaded it from Source Forge, unzipped it and copied it into one of my website folders.  I then modified a virtual host to redirect the sub-domain "phppgadmin.example.com" to the folder.

* I can access the folder via the sub-domain and all appears to be working fine.

* I've disabled the "extra security" flag to allow login's via postgres.

* I've logged into psql and updated my postgres user password.

* phpPgAdmin and PostgreSQL are on the same box.

My pg_hba.conf file looks like this...

```

# "local" is for Unix domain socket connections only
local  all  postgres ident sameuser
local all all password
# IPv4 local connections:
host all all 127.0.0.1/32  md5
# IPv6 local connections:
host all all ::1/128  md5
``` 

my pg_ident.conf file has nothing but comments.


Any ideas?

*edit*
Actually, during the writing of this, I found out what the problem was, but I thought I'd post for future reference in case anyone else has this problem.

In the phpPgAdmin config.inc.php file, I updated this variable...

```
// Hostname or IP address for server.  Use '' for UNIX domain socket.
// use 'localhost' for TCP/IP connection on this computer
$conf['servers'][0]['host'] = '';
```

to
```
// Hostname or IP address for server.  Use '' for UNIX domain socket.
// use 'localhost' for TCP/IP connection on this computer
$conf['servers'][0]['host'] = 'localhost';
```

However, might anyone explain why Unix domain socket wasn't working?

Cheers,
Fozzy

---

