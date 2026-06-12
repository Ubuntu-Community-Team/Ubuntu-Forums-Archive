---
title: "Mysql access denied for the mysql user"
date: 2008-06-11
forum: General Help
---

### Post by Dennis Wilson on 2008-06-11
Sorry to bother, but I am new to Ubuntu. I have installed version 7.10 on a laptop and am generally happy with it.

I am however having issues with my sql. It will install but, I can not connect. My access is denied. I have searched the web and found that it could be an issue with apparmor which I uninstalled. This did not help. The error is consistent. I also have Firestarter installed. I did create a rule allowing access to the port 3306 on localhost.

I installed both using the synaptic installer and the apt-get process. Neither seemed to work.

I am wondering if I would be better off building mysql from source and installing it.

Thanks in advance for your time.

---

### Post by ibutho on 2008-06-11
Hi.

Follow the howto on this [page]("https://help.ubuntu.com/community/ApacheMySQLPHP"). Follow the instructions for installing and configuring (the part labeled "after mysql") mysql 5 and hopefully that will resolve your problem.

---

### Post by p_quarles on 2008-06-12
How are you attempting to access the MySQL server? What application(s) is/are using it? Have you created a user -- and granted it access to the appropriate databases -- for those applications?

---

### Post by Dennis Wilson on 2008-06-12
The short answer is that I was using the following command once the install was complete
mysql -h localhost -u mysql -p

I did grep the ps -ef output and mysqld was running. 

What I found on the Ubuntu forums linked apparmor to the issue, but an uninstall of that app and a reboot did nothing. I tried stopping my Firestarter but that did not help.

I tried starting the mysqld with --ignore-grant-tables but I got the same error as with mysql.

I tried to use mysqladmin but the only thing that it would do is give me a verbose help listing. It would do nothing else.

When I checked /etc/passwd, mysql was in there. When I checked /etc/group the group mysql was there, too. The grants/permissions on the directories showed mysql as both owner and group. 

I tried adding the root password to the my.cnf for the user mysql. That also did nothing.

So, about 9:00 pm I ran out of things to try. :-(

I am running an Ubuntu 7.10 that was upgraded from 7.04.

Thanks for the replies.

---

### Post by p_quarles on 2008-06-12
The way I've always created new MySQL users is via the root MySQL user's shell. To reset the root password, you can run:
```
sudo dpkg-reconfigure mysql-server
```
Then, log in (with the following command) and run any maintenance you need to:
```
mysql -u root -p
```

---

### Post by Dennis Wilson on 2008-06-13
Thanks for the reply.

This is the result:

dennis@dennis-laptop:~$ sudo dpkg-reconfigure mysql-server
[sudo] password for dennis:
dennis@dennis-laptop:~$ mysql -u root -p
Enter password: 
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

I am not sure I understand if there should be some kind of action I should see after running the dpkg-reconfigure command. It seemed to run very fast and did not query me for any input. I had assumed that I would be asked to enter a password or something?

---

