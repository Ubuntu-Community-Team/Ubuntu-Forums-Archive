---
title: "mysql error running synaptic package manager"
date: 2008-02-25
forum: General Help
---

### Post by vosons2008 on 2008-02-25
I have the problem below every time I run synaptic package manager (example shows installation of firestarter)
The program installs but the error messages below appear

Couple of questions:
Why is synaptic trying to access mysql.
How do I configure either mysql or synaptic so that the error does not occur.
Can I configure synaptic to not access mysql

Thanks,


(Reading database ... 95753 files and directories currently installed.)
Preparing to replace firestarter 1.0.3-6ubuntu1 (using .../firestarter_1.0.3-6ubuntu1_i386.deb) ...
Unpacking replacement firestarter ...
Setting up mydns-mysql (1:1.1.0-8) ...
/etc/mydns.conf created/modified. See mydns.conf(5) for details.
A backup of the old config file is at /etc/mydns.conf.dpkg-old. Values
were preserved, except for database (database,db-*)
and distribution-specific information (user, group, pidfile).
ERROR 1045 (28000): Access denied for user 'name'@'cmp-desktop' (using password: YES)
Creating database...
mysqladmin: connect to server at 'cmp-desktop' failed
error: 'Access denied for user 'name'@'cmp-desktop' (using password: YES)'
dpkg: error processing mydns-mysql (--configure):
 subprocess post-installation script returned error exit status 1
Setting up firestarter (1.0.3-6ubuntu1) ...
Firewall script saved as /etc/firestarter/firewall
 * Stopping the Firestarter firewall...
   ...done.
 * Starting the Firestarter firewall...
   ...done.

---

