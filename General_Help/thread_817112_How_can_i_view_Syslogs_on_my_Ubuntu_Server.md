---
title: "How can i view Syslogs on my Ubuntu Server?"
date: 2008-06-03
forum: General Help
---

### Post by markbusu on 2008-06-03
Thanks!

---

### Post by lok on 2008-06-03
Is this a local or remote server?

If it is local and you have gnome running try 
System > Administration > System Log
Or
run 'gnome-system-log'

If you don't have X running on the server and/or it's remote go to /var/log/
and use 'less' or whatever pager you want to read through syslog

---

