---
title: "MySQL Administrator connection woes"
date: 2008-05-16
forum: General Help
---

### Post by RagingAardvark on 2008-05-16
Hi folks,
I have installed MySQL on a remote 8.04 server and connect to it locally fine. 

I have followed the various instructions and commented out the 127.0.0.1 in /etc/mysql/my.cnf, used ; 

 GRANT ALL PRIVILEGES ON *.* TO root@'130.0.0.0/255.0.0.0';
GRANT ALL PRIVILEGES ON *.* TO auser@'130.0.0.0/255.0.0.0';
CREATE USER 'user'@'%' IDENTIFIED BY 'password';
GRANT ALL PRIVILEGES ON *.* TO `user`@`%` IDENTIFIED BY 'password';
FLUSH PRIVILEGES;

restarted the MySql on the remote server and still get the cannot connect 2003 message from my local 8.04 desktop session using MySQL Administrator.

I can SSH to the server OK (hence being able to try all of the above)

I'm pretty much out of ideas here. Help please!

TIA

KJ

---

### Post by Monicker on 2008-05-16
Is your bind-address in my.cnf set to the ip of the mysql server itself?  What is the full error message?  Also, check /var/log/mysql.log and /var/log/mysql.err for more details.

---

### Post by RagingAardvark on 2008-05-19
I tried setting the bind-address to the IP of the server, and also commenting out the bind-address line. 

There is nothing in mysql.log and nothing in mysql.err

The first time I try to connect, I get ;

Could not connect to host 'blah'
MySQL Error Nr. 1045
Access denied for user 'root'@'somewhere' (using password: YES)

So, I went into the server and added ;

GRANT ALL PRIVILEGES on *.* TO 'root'@'somewhere' ;
FLUSH PRIVILEGES

sudo /etc/init.d/mysql restart


... the same thing happened. 

I also tried GRANT ALL PRIVILEGES on *.* TO 'root'@'somewhere' IDNETIFIED BY 'password' ;

.... the same again!

---

### Post by photostyle on 2008-06-27
I was having the same issue. managed to fix it.

After doing several different variations on the 'grant all' command, I looked at the user table and saw that several more root user accounts had been created with variation on the host. By default, it seems there is 3 root accounts, with the following host values: localhost, %hostname%, 127.0.0.1


I deleted the extra root acounts, leaving just those three.

Then I created a new user as follows:

create user 'root'@'%' identified by 'password';

Then granted permissions:

grant all on *.* to 'root'@'%' identified by 'password';
flush privileges;

Restarted mysql and was able to connect remotely. Hopefully this will help everyone else.

---

