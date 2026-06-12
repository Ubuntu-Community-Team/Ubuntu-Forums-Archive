---
title: "Problem on installing apache-tomcat"
date: 2016-05-09
forum: General Help
---

### Post by satimis on 2016-05-09
Hi all,

Ubuntu 16.04 desktop

I follow;
How To Install Apache Tomcat 8 on Ubuntu 16.04
[https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-install-apache-tomcat-8-on-ubuntu-16-04)

to install apache-tomcat

Step 4: Update Permissions
&#10219; cd /opt/tomcat
&#10219; sudo chgrp -R tomcat conf
&#10219; sudo chmod g+rwx conf
&#10219; sudo chmod g+r conf/*```

chmod: cannot access 'conf/*': No such file or directory

```

&#10219; ls -l```

total 112
drwxr-x--- 2 root root    4096 May  9 22:54 bin
drwxrwx--- 2 root tomcat  4096 Mar 12 19:41 conf
drwxr-x--- 2 root root    4096 May  9 22:54 lib
-rw-r----- 1 root root   57092 Mar 12 19:41 LICENSE
drwxr-x--- 2 root root    4096 Mar 12 19:40 logs
-rw-r----- 1 root root    1804 Mar 12 19:41 NOTICE
-rw-r----- 1 root root    6738 Mar 12 19:41 RELEASE-NOTES
-rw-r----- 1 root root   15946 Mar 12 19:41 RUNNING.txt
drwxr-x--- 2 root root    4096 May  9 22:54 temp
drwxr-x--- 7 root root    4096 Mar 12 19:41 webapps
drwxr-x--- 2 root root    4096 Mar 12 19:40 work
```

&#10219; ls -ald conf```

drwxrwx--- 2 root tomcat 4096 Mar 12 19:41 conf

```

&#10219; sudo ls -al conf/```

total 228
drwxrwx--- 2 root tomcat   4096 Mar 12 19:41 .
drwxr-xr-x 9 root root     4096 May  9 22:54 ..
-rw------- 1 root tomcat  12209 Mar 12 19:41 catalina.policy
-rw------- 1 root tomcat   7123 Mar 12 19:41 catalina.properties
-rw------- 1 root tomcat   1338 Mar 12 19:41 context.xml
-rw------- 1 root tomcat   1149 Mar 12 19:41 jaspic-providers.xml
-rw------- 1 root tomcat   2359 Mar 12 19:41 jaspic-providers.xsd
-rw------- 1 root tomcat   3622 Mar 12 19:41 logging.properties
-rw------- 1 root tomcat   7308 Mar 12 19:41 server.xml
-rw------- 1 root tomcat   2164 Mar 12 19:41 tomcat-users.xml
-rw------- 1 root tomcat   2634 Mar 12 19:41 tomcat-users.xsd
-rw------- 1 root tomcat 168582 Mar 12 19:41 web.xml

```

Please help.  Thanks

Regards
satimis

---

### Post by Azdour on 2016-05-09
Hi,

I think you need to the -R recursive parameter on the chmod command.  

Run:

> man chmod

You cannot use wildcards e.g the '*' character.  Use the -R parameter to apply the setting to everything within conf:
> 
sudo chmod -R g+r conf

---

### Post by satimis on 2016-05-09
> **Azdour said:**
> Hi,

I think you need to the -R recursive parameter on the chmod command.  

Run:



You cannot use wildcards e.g the '*' character.  Use the -R parameter to apply the setting to everything within conf:
Hi,

Performed following step;

&#10219; sudo chmod -R g+r conf/
[sudo] password for satimis: 
no complaint

&#10219; sudo ls -al conf/```

total 228
drwxrwx--- 2 root tomcat   4096 Mar 12 19:41 .
drwxr-xr-x 9 root root     4096 May  9 22:54 ..
-rw-r----- 1 root tomcat  12209 Mar 12 19:41 catalina.policy
-rw-r----- 1 root tomcat   7123 Mar 12 19:41 catalina.properties
-rw-r----- 1 root tomcat   1338 Mar 12 19:41 context.xml
-rw-r----- 1 root tomcat   1149 Mar 12 19:41 jaspic-providers.xml
-rw-r----- 1 root tomcat   2359 Mar 12 19:41 jaspic-providers.xsd
-rw-r----- 1 root tomcat   3622 Mar 12 19:41 logging.properties
-rw-r----- 1 root tomcat   7308 Mar 12 19:41 server.xml
-rw-r----- 1 root tomcat   2164 Mar 12 19:41 tomcat-users.xml
-rw-r----- 1 root tomcat   2634 Mar 12 19:41 tomcat-users.xsd
-rw-r----- 1 root tomcat 168582 Mar 12 19:41 web.xml

```

Thanks

satimis

---

