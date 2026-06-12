---
title: "server down"
date: 2007-06-04
forum: General Help
---

### Post by madamek on 2007-06-04
my server went down yesterday - my class project is due tomorrow!

i was pulling a lot of information from a small database when all access was stopped - ssh connection refused. after a restart i am getting a 'Segmentation fault' error.  Apache2 has been started and restarted but serves nothing.  i can't access mysql database message: 'Can't connect to local MySQL server through socket /var/run/mysqld/mysqld.sock (13)' 

Any help is greatly appreciated!

---

### Post by madamek on 2007-06-04
Apache2 is BACK!  But ssh and MySQL are still out!

when I try to access MySQL i get this message - Could not connect to
MySQL: Can't connect to local MySQL server through socket
'/var/run/mysqld/mysqld.sock' (13)

---

### Post by cornsnap on 2007-06-04
check /var/log/messages for any indication of the cause of the initial failure.

---

### Post by madamek on 2007-06-04
/var/log/messages: Permission denied

I've been searching for error logs for awhile now but can't find em.

---

### Post by madamek on 2007-06-04
something new i found is that the Segmentation fault error pops up when I try to /etc/init.d/ssh start

when i try to ssh into the machine i am back to getting 'connection refused'

---

