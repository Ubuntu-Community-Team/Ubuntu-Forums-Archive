---
title: "mysql security"
date: 2013-03-13
forum: General Help
---

### Post by cbillson on 2013-03-13
basic install of mysql, when typing 'mysql' at CLI, you get a (mysql) prompt. moving from here requires rights elevation.

is it possible to secure this prompt, and are there any security concerns leaving it accessible?

Cheers
Chris

---

### Post by Habitual on 2013-03-13
[http://manpages.ubuntu.com/manpages/precise/man1/mysql_secure_installation.1.html](http://manpages.ubuntu.com/manpages/precise/man1/mysql_secure_installation.1.html)

---

### Post by slickymaster on 2013-03-13
> **Habitual said:**
> [http://manpages.ubuntu.com/manpages/precise/man1/mysql_secure_installation.1.html](http://manpages.ubuntu.com/manpages/precise/man1/mysql_secure_installation.1.html)

Exactly.

A default Linux MySQL installation isn't necessarily secure but this script increases it's default security. To run it, just open a terminal window as root (either using sudo or su -) and type:
```
mysql_secure_installation
```
The script will then guide you through several steps to lockdown your MySQL installation.
The first step is to set the root password. By default a root password isn't set, so to set it, hit Enter when asked for the current password (meaning blank) and then set the password as directed. Setting the root password ensures that nobody can log into the MySQL root user without the proper authorization.
Then, remove anonymous users. By default, a MySQL has an anonymous user, allowing anyone to log into MySQL without having to have a user account. This is just for testing.
Disable non-local root access to ensure that the root user can not login over the network (and allow root connections only from the local machine).
Finally remove the test database and access rules related to it. MySQL comes with a database named &#8216;test&#8217; that anyone can access. This is also intended only for testing, and should be removed before moving into a production environment.

---

