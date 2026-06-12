---
title: "Firebird2.5 Connect Problem"
date: 2016-06-24
forum: General Help
---

### Post by joe203 on 2016-06-24
I am new to Ubuntu and am trying to get Firebird2.5 running on 16.04 64bit.
I have searched the web, but cannot find any real help - only examples of what
has already failed for me.

FB install went fine & I see the example employee.fdb file in /var/lib/firebird/2.5/data

I try to connect using:

```
sudo isql-fb
 Use CONNECT or CREATE DATABASE to specify a database
 SQL> connect "/var/lib/firebird/2.5/data/employee.fdb " user 'SYSDBA' password '*****'
CON> 
```

Obviously what is missing is this response:
```
Database:  "/var/lib/firebird/2.5/data/employee.fdb ", User: SYSDBA
 SQL>

Any help will be much
``` appreciated. TIA, Joe

---

