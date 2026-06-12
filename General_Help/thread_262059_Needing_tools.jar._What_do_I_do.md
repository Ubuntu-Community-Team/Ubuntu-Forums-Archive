---
title: "Needing tools.jar. What do I do?"
date: 2006-09-21
forum: General Help
---

### Post by moufranica on 2006-09-21
Dear Gurus,
I am installing sipxpbx and after running it I get this.

```

user@ubuntuserver:/$ sudo /etc/init.d/sipxpbx start
Checking rpm configuration file updates:success

Checking apache:failure

Checking hostname:failure

Checking /etc/hosts file:success

Checking ssl configuration:failure

Checking watchdog:success

Checking sipproxy:success

Checking sipxconfig:failure

Checking sipXvxml:success

Checking sipxpark:success

Checking sipxpresence:success

Checking sipstatus:success

Checking sipregistrar:success

Checking sipauthproxy:success

Checking keepalive:success

sipXpbx:
sipXpbx: sipXpbx configuration problems found:
sipXpbx:
sipXpbx: Check apache
sipXpbx:    Syntax error on line 235 of /etc/sipxpbx/httpd.conf:
sipXpbx: module access_module is built-in and can't be loaded
sipXpbx:
sipXpbx: Check hostname
sipXpbx:    Hostname ubuntuserver is not qualified.
sipXpbx:
sipXpbx: Check ssl configuration
sipXpbx:        SSL key and/or certificate not found (/etc/sipxpbx/ssl/ssl.{key,
crt})
sipXpbx:
sipXpbx:     See instructions in /usr/share/doc/sipxcommserverlib-3.4.0/INSTALL.
ssl
sipXpbx:
sipXpbx: Check sipxconfig
sipXpbx:    psql: FATAL:  Ident authentication failed for user "postgres"
sipXpbx:
Attempting to start despite configuration problems

Starting sipXpbx:
Starting watchdog: success

 Waiting for keepalive to start: 20 19 18 17 16 success

Starting httpd: Syntax error on line 235 of /etc/sipxpbx/httpd.conf:
module access_module is built-in and can't be loaded
failure

```

On top of this when I run **/usr/bin/sipxconfig.sh --setup** I get this:
```

user@ubuntuserver:/usr/bin$ sudo /usr/bin/sipxconfig.sh --setup
psql: FATAL:  Ident authentication failed for user "postgres"
 * Starting PostgreSQL 7.4 database server                                                             [ ok ]
psql: FATAL:  Ident authentication failed for user "postgres"
*** Optional check for tools.jar, OK if not found...
Unable to locate tools.jar. Expected to find it in /usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/lib/tools.jar
createdb: could not connect to database postgres: FATAL:  Ident authentication failed for user "postgres"

BUILD FAILED
/etc/sipxpbx/database/database.xml:58: exec returned: 1

Total time: 4 seconds
user@ubuntuserver:/usr/bin$


```

How do I get tools.jar installed? I am also not sure if bind is needed? Thanks in advance.

---

### Post by hw-tph on 2006-09-21
Switch to Sun's Java instead of gcj. Install it if you do not have it already (**sudo apt-get install sun-j2sdk1.5**) and then switch to Sun's Java (**sudo update-alternatives --config java** and select j2sdk1.5-sun.


Håkan

---

### Post by moufranica on 2006-09-21
I assume I have to create a symbolic link to where ever tools.jar is after installing sunjava?

---

