---
title: "Access denied for user 'root'@'192.168.101.141' (using password: YES)"
date: 2018-06-10
forum: General Help
---

### Post by ylafont on 2018-06-10
I have to be missing something that i am not aware off  when trying to access MYSQL from a remote machine. 

MY SQL services are  ok
```
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: active (running) since Sun 2018-06-10 21:10:18 EDT; 25min ago
  Process: 1080 ExecStart=/usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid (code=exited, status=0/SUCCESS)
  Process: 1035 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=0/SUCCESS)
 Main PID: 1083 (mysqld)
    Tasks: 30 (limit: 4915)
   CGroup: /system.slice/mysql.service
           &#9492;&#9472;1083 /usr/sbin/mysqld --daemonize --pid-file=/run/mysqld/mysqld.pid

Jun 10 21:10:17 EclipseTwo systemd[1]: Starting MySQL Community Server...
Jun 10 21:10:18 EclipseTwo systemd[1]: Started MySQL Community Server.

```

i have a commented out

```
#bind-address          = 0.0.0.0  

```
in /etc/mysql/mysql.conf.d/mysqld.cnf

I am able to authenticate locally via SSH  with 

```
mysql -h localhost -u root -p
```

and I have granted access to user 

```
GRANT ALL ON *.* TO 'root'@'localhost' IDENTIFIED BY 'rootpassword' WITH GRANT OPTION;
FLUSH PRIVILEGE;

```

but yet I cannot access MYSQl remotely via workbench

```
2018-06-11T01:11:33.700388Z 5 [Note] Access denied for user 'root'@'192.168.101.141' (using password: YES)
2018-06-11T01:11:38.960074Z 6 [Note] Access denied for user 'root'@'192.168.101.141' (using password: YES)


```

and i have also disable the firewall. What have i missed?  Anyone know?

I think i have accounted for everything. Any assistance greatly appreciated.

---

### Post by QIII on 2018-06-10
Are you able to establish an ssh connection to the remote machine via the terminal?

(By the way, it is a very bad idea to allow root logins via ssh.  It is also bad to use passwords with ssh.  I would recommend the use of keys.)

---

### Post by ylafont on 2018-06-10
actually -  "root" is the MYSQL user  -   I login in via ssh with another user account with root privileges.

---

### Post by QIII on 2018-06-10
I wouldn't recommend using the root MySQL user, either.

OK.  How did you set up your connection in Workbench?

---

### Post by ylafont on 2018-06-11
Nothing special with workbench -  

Connection Method - Standard (tcp/ip)
IP of machine and port of 3306

[IMG]https://eclipsephoto.net/nextcloud/index.php/s/drqbkSePrXBrakn[/IMG]

---

### Post by SeijiSensei on 2018-06-11
MySQL uses both usernames and source IPs when determining access.  'root'@'localhost' is not the same as 'root'@'192.168.101.141'.  See [https://dev.mysql.com/doc/refman/5.7/en/account-names.html](https://dev.mysql.com/doc/refman/5.7/en/account-names.html).

---

### Post by ylafont on 2018-06-11
> **SeijiSensei said:**
> MySQL uses both usernames and source IPs when determining access.  'root'@'localhost' is not the same as 'root'@'192.168.101.141'.  See [https://dev.mysql.com/doc/refman/5.7/en/account-names.html](https://dev.mysql.com/doc/refman/5.7/en/account-names.html).


When you are right, you are right.  I thought i took that into consideration.  I guess some time one gets lost in the weeds, I modified the command to allow remote access from all IP's as follows

```
GRANT ALL PRIVILEGES ON *.* TO 'rootuser'@'%' IDENTIFIED BY 'rootpassword' WITH GRANT OPTION;
```

thank you!

---

