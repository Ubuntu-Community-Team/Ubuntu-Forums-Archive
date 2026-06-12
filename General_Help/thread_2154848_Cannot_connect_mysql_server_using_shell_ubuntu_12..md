---
title: "Cannot connect mysql server using shell ubuntu 12.04"
date: 2013-06-16
forum: General Help
---

### Post by Saiede on 2013-06-16
I cannot connect mysql server using shell. My ubuntu system is 12.04. I have tried this several times and read some threads related to this and tried in various ways. But no hope. It shows the following error. Can anyone please help. 

[FONT=courier new]root@sayeed-laptop:/var/log#  sudo mysql -u root -
ERROR 2002 (HY000): Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)
root@sayeed-laptop:/var/log# [/FONT]

Thanks and Regards, 
Saiede

---

### Post by prodigy_ on 2013-06-16
```
sudo service mysql start

# type your MySQL root password after the "=" character:
mysql -u root --password=
```
Note that you don't need **sudo** to connect to MySQL.

---

### Post by Saiede on 2013-06-16
> **prodigy_ said:**
> ```
sudo service mysql start

# type your MySQL root password after the "=" character:
mysql -u root --password=
```
Note that you don't need **sudo** to connect to MySQL.

Hello, 

I have tried as you advised. But shows the following error:

root@sayeed-laptop:/opt/lampp/htdocs# service mysql start
mysql: unrecognized service

---

### Post by prodigy_ on 2013-06-16
Did you install it at all? If not:
```
sudo apt-get install mysql-server
```

And you probably want to read this first:
[https://help.ubuntu.com/12.04/serverguide/mysql.html](https://help.ubuntu.com/12.04/serverguide/mysql.html)

---

### Post by Saiede on 2013-06-16
@ [**[COLOR=#000000]prodigy_[/COLOR]**]("http://ubuntuforums.org/member.php?u=518500") 	 

I have installed lampp stack. Here goes a question does it make any sense to install mysql server using command line?

For a clear visibility I can access mysql server using php myadmin on my laptop, but I cannot connect it using shell prompt.

---

### Post by prodigy_ on 2013-06-16
That's strange. Are you sure the server is installed on your laptop and not on some other machine? In case of the latter you need to make sure that MySQL port (default 3306) is either forwarded ([e.g. through an SSH connection](https://help.ubuntu.com/community/SSH/OpenSSH/PortForwarding)) or bound to an IP other than 127.0.0.1.

To a forwarded port you can connect as if the service were running locally. To connect to the service running on a remote host directly: ```
mysql -h hostname_or_IP_address -p port -u username -ppassword # substitute actual hostname, username and password
```

---

### Post by Saiede on 2013-06-17
Dear [**[COLOR=#000000]prodigy_[/COLOR]**]("http://ubuntuforums.org/member.php?u=518500"), 

Thank you very much for quick help and advise. I can now connect with mysql server. Many Thanks :).

---

