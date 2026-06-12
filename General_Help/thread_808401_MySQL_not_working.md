---
title: "MySQL not working"
date: 2008-05-26
forum: General Help
---

### Post by z662 on 2008-05-26
I am not sure if I have not properly understood threads already posted on this forum and others, in regards to getting MySQL working. However, I can not get it to reset the root password and its driving me nuts!  I am running Ubuntu server 8.04 and Ill post any thing you need as far as the results of everything I have tried...Thanks in advance 

After a fresh installation, I can login with the simple:

username@host:~$ mysql

so after exiting,

If I want to try and create a password or anything by trying mysql -u root -p password NEWPASSWORD, or any type of variation, I get this error message 

mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)

***I just want to be able to create a root password so that I may be able to create an additional account that can be used to cgi scripts and will not have to rely on using the root account.

---

### Post by TeoBigusGeekus on 2008-05-26
Download MySQL Administrator, it's in the repositories. It makes handling MySQL a piece of cake.

---

### Post by Monicker on 2008-05-26
This is what you should be using
```

mysqladmin password "newpassword"
```

---

### Post by z662 on 2008-05-26
Thanks for the quick response, however, 

username@host:~$ mysqladmin password "new"
mysqladmin: Can't turn off logging; error: 'Access denied; you need the SUPER privilege for this operation'

username@host:~$ sudo mysqladmin password "new"
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Any ideas?

---

### Post by Monicker on 2008-05-26
> **z662 said:**
> Thanks for the quick response, however, 

username@host:~$ mysqladmin password "new"
mysqladmin: Can't turn off logging; error: 'Access denied; you need the SUPER privilege for this operation'

username@host:~$ sudo mysqladmin password "new"
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'


Any ideas?

Did you install the ubuntu mysql package?  Ubuntu and debian prompt you to set the root password when it is installing the package.  How and from where exactly did you install mysql?

---

### Post by AndrewTheArt on 2008-05-26
I've had issues with this and I recall these steps working - (I had to modify the commands a bit to make things run smoothly)

> First things first. Log in as root and stop the mysql daemon. 
[B]
sudo /etc/init.d/mysql stop[/B] 

Now lets start up the mysql daemon and skip the grant tables which store the passwords.

**sudo mysqld_safe --skip-grant-tables&**

(press Ctrl+C now to disown the process and start typing commands again)

You should see mysqld start up successfully. If not, well you have bigger issues. Now you should be able to connect to mysql without a password.

[B]sudo mysql --user=root mysql

update user set Password=PASSWORD('new-password');
flush privileges;
exit;[/B] 

Now kill your running mysqld then restart it normally. 

**sudo killall mysqld_safe&**
(press Ctrl+C now to disown the process and start typing commands again)
[B]/etc/init.d/mysql start

[/B]You should be good to go. Try not to forget your password again.
[http://www.howtoforge.com/reset-forgotten-mysql-root-password](http://www.howtoforge.com/reset-forgotten-mysql-root-password)

---

### Post by z662 on 2008-05-26
I followed your steps Andrew, exactly as they were and everything seemed to work.  However I could still sign in with no password as root.  I then decided to just completely remove mysql-server-5.0 with "sudo dpkg -P mysql-server-5.0" after re-installing, it asked me for the root password to use, so I entered my password and AGAIN, when I would type "mysql" from the command line it would sign me in without asking for a password.  I am rather confused now....is it signing me in as someone else than root? Perhaps mysql or something???

On a further note if I try to sign in as root, this is what happens

username@host:~$ mysql -u root
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: NO)


Thanks for the replies

---

### Post by z662 on 2008-05-26
I finally figured out the 'problem'. I did not know that there was an anonymous user created by default that allowed access with no password so i used 'DELETE FROM user WHERE user =''; and FLUSH PRIVILEGES; to remove that...I now must specify a password to sign in....Thanks for all your help everyone, your thoughts led me to figure out the answer via google...thank you again

---

