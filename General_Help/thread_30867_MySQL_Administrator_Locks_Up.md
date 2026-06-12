---
title: "MySQL Administrator Locks Up"
date: 2005-04-30
forum: General Help
---

### Post by ForwardProgress on 2005-04-30
Hello all -

I am running Hoary (i386) and installed the MySQL Package along with MySQL Administrator (mysql-admin) package.  When I run MySQL Administrator on my localhost and move between the views it always locks up on the 2nd or 3rd view I choose.

The only way I have found around this problem is to log into MySQL via phpMyAdmin on my localhost at the same time.  The MySQL Administrator then runs fine and I can switch between the various views with no problems.

So, it appears my MySQL Administrator login session is dropping out unless I have a separate session going via phpMyAdmin.

Any ideas as to what the problem is and how I can fix it?

Thanks much for any ideas you may have.

---

### Post by ForwardProgress on 2005-05-14
:-P Problem has corrected itself - not sure if this is due to one of the auto-updates I have applied?  Regardless - all is now well.

---

### Post by FutureProspects on 2005-07-24
Hi,

I'm experiencing the same problems (lockups) using Hoary (i386 and i686).  mysql-admin locks up during remote and local connections.

I'm using mysql-admin version 1.0.18-1 against a local mysql-server version 4.0.23-3ubuntu2 and remote slackware mysql server version 4.0.23a 

I can connect to the slackware mysql using mysql-admin on a Windows machine without any problems.

Any ideas...???

---

