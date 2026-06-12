---
title: "Installing mysql 5 problems"
date: 2008-07-01
forum: General Help
---

### Post by -=Mizo=- on 2008-07-01
Hello,,,
I am trying to install mysql and that's what i am getting:
> 
root@ubuntu:/# sudo apt-get install mysql-server-5.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mysql-server-5.0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mysql-server-5.0 (5.0.51a-3ubuntu5) ...
 * Stopping MySQL database server mysqld                                                                                                     /usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
                                                                                                                                      [ OK ]
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
Reloading AppArmor profiles : done.
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
 * Starting MySQL database server mysqld                                                                                                     /usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
                                                                                                                                      [fail]
invoke-rc.d: initscript mysql, action "start" failed.
dpkg: error processing mysql-server-5.0 (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 mysql-server-5.0
E: Sub-process /usr/bin/dpkg returned an error code (1)



any idea?

---

### Post by justleen on 2008-07-01
mysql-server-5.0 is already the newest version.


its already installed, for one.. 

the errors you see are due to stopping and starting mysqld

does this give any errors? :
```
/etc/init.d/mysqld restart 
```

---

### Post by -=Mizo=- on 2008-07-01
root@ubuntu:/# /etc/init.d/mysqld restart
-bash: /etc/init.d/mysqld: No such file or directory

---

### Post by -=Mizo=- on 2008-07-01
root@ubuntu:/# /etc/init.d/mysql restart 


> 
root@ubuntu:/etc/init.d# /etc/init.d/mysql restart
 * Stopping MySQL database server mysqld                                                                                                     /usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
                                                                                                                                      [ OK ]
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
 * Starting MySQL database server mysqld                                                                                                     /usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied
/usr/sbin/mysqld: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: cannot apply additional memory protection after relocation: Permission denied



---

### Post by -=Mizo=- on 2008-07-01
:confused:any 1 :confused:

---

### Post by -=Mizo=- on 2008-07-01
:(I really need help in this i got to do some projects in With mysql
any help will be appreciated

---

