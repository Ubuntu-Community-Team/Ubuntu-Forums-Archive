---
title: "can't start MariaDB on Ubuntu 18.04"
date: 2019-05-25
forum: General Help
---

### Post by megunticook on 2019-05-25
I'm setting up a development web server on my computer running Ubuntu 18.04 on the Windows 10 subsystem. Have NGINX and PHP set up fine, but keep stumbling with MariaDB--I can install it but can't get it to start. I tried checking the error log at /var/log/mysql/mariadb-bin.000001 but it's just a few indecipherable lines and my text editor (Nano) says "Converted from Mac format."

Tried uninstalling and reinstalling MariaDB but same result.

Any suggestions? Thanks for your help.

Here's what I'm seeing when I try to view the error log:

```
&#65533;bin4G&#65533;\^O^A^@^@^@&#65533;^@^@^@^@^A^@^@^@^@^D^@10.3.15-MariaDB-1:10.3.15+maria~bionic-log^@^@^@^@^@^@^@^@4G&#65533;\^S8
^@^H^@^R^@^D^D^D^D^R^@^@&#65533;^@^D^Z^H^@^@^@^H^H^H^B^@^@^@




^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@^@$^H^H^H




^A&#65533;&#65533;^Y&#65533;4G&#65533;\&#65533;^A^@^@^@^]^@^@^@^]^A^@^@^@^@^@^@^@^@^@^@s&#65533;&#65533;&#65533;4G&#65533;\&#65533;^A^@^@^@-^@^@^@J^A^@^@^@^@^R^@^@^@mariadb-bin.000001&#65533;^[^G&#65533;4G&#65533;\^C^A^@^@^@^W^@^@^$






[ Read 9 lines (Converted from Mac format) ]

```

---

### Post by megunticook on 2019-05-25
I tried another approach, this time installing MariaDB from the Ubuntu repository. Still can't start the service, but at least now I can read the error log. I found this error:

```
2019-05-25 10:24:47 7f5fb49f0c80 InnoDB: Error: Linux Native AIO interface is not supported on this platform. Please check your OS documentation and install appropriate binary of InnoDB.
InnoDB: You can disable Linux Native AIO by setting innodb_use_native_aio = 0 in my.cnf

```

Why am I getting this error? I've installed MariaDB on Ubuntu 18.04 before, never seen this issue. How do "install appropriate binary of InnoDB"? 

Thanks.

---

### Post by megunticook on 2019-05-25
Figured it out--had to stop the MySQL service running on Windows which apparently was interfering with MariaDB in the Ubuntu subsystem.

---

