---
title: "FTP super admin permissions"
date: 2013-04-09
forum: General Help
---

### Post by roe74979 on 2013-04-09
hello all,

I was wondering if there was a way to give 1 user complete control over all of FTP?  I know that there are risks, but its a project and when I graduate in 30 days my professors will take it over.  So I need to create a super admin over all FTP related files. I can give each file permissions, but i cant figure out how to give 1 person all permissions

im using Ubuntu 12.10
proftpd using webmin for management

thanks!

---

### Post by rnerwein on 2013-04-09
> **roe74979 said:**
> hello all,

I was wondering if there was a way to give 1 user complete control over all of FTP?  I know that there are risks, but its a project and when I graduate in 30 days my professors will take it over.  So I need to create a super admin over all FTP related files. I can give each file permissions, but i cant figure out how to give 1 person all permissions

im using Ubuntu 12.10
proftpd using webmin for management

thanks!
hi
if you realy want it: you have to insert, at the last !!!!! line, in /etc/sudoers:

desired_username   ALL=NOPASSWD: /usr/bin/ftp

and for sure - this only works for your lokal system ;-)
and if this user use some exclemation mark - he will be super user on the system !!
!!!! at your own risk !!!!
ciao

---

