---
title: "Question on SELinux"
date: 2006-10-23
forum: General Help
---

### Post by 25an on 2006-10-23
Hi!
I am having some problem with running javawebmail on tomcat. Even though I have a given rwx rights to all on a dir that javawebmail is trying to write to I get access denied. I den happened to stumble on SELinux and found that SELinux has been integrated into version 2.6 series of the Linux kernel. Could it be SELinux that is stopping javawebmail to get permission even though I have given all the rights to every one?
It is the webapps dir that javawebmail is trying to write a file to.

par@asus2:/var/lib/tomcat5$ ll
total 16
drwxr-x--- 3 tomcat5 adm  4096 2006-10-23 10:07 conf
lrwxrwxrwx 1 root    root   17 2006-10-21 19:54 logs -> ../../log/tomcat5
drwxr-xr-x 4 root    root 4096 2006-10-21 19:54 shared
drwxr-xr-x 2 tomcat5 root 4096 2006-10-23 10:07 temp
drwxrwxrwx 9 tomcat5 root 4096 2006-10-22 22:46 webapps
lrwxrwxrwx 1 root    root   19 2006-10-21 19:54 work -> ../../cache/tomcat5

---

### Post by raycast on 2007-04-01
Ubuntu does not enable SELinux by default, so it is not the cause. Instead you probably need to configure the Java Security Manger differently.

---

