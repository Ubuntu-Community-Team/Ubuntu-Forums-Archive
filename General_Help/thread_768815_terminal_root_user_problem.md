---
title: "terminal root user problem"
date: 2008-04-26
forum: General Help
---

### Post by Periswell on 2008-04-26
hi

i have a problem with my terminal that when ever i do the sudo su and put in my password to get to root user, whatever button i press after loging in it automatically exits out of root. eg...

> joshua@utnubu:~$sudo su
password:*****
root@utunbu: (whatever button)exit

eg the last bit could be...

> root@utunbu:gexit

this is very annoying so please could someone help.

-josh

---

### Post by ysangkok on 2011-05-19
If the root users standard shell is not usable you can specify another. Try "sudo su -c /bin/sh"

---

