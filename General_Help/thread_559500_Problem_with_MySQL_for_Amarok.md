---
title: "Problem with MySQL for Amarok"
date: 2007-09-25
forum: General Help
---

### Post by wersdaluv on 2007-09-25
I was trying to use MySQL for Amarok by following this howto--> [http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

I do not know what went wrong but according to Amarok, > MySQL reported the following error:
Access denied for user 'amarok'@'localhost' (using password: YES)
You can configure MySQL in the Collection section under Settings->Configure Amarok

Any ideas?

---

### Post by jamvegan on 2007-09-25
Do the username (amarok) and the password (whatever you made up) match when you ran this:
```
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
```
and when you entered the configuration in amarok?

---

### Post by wersdaluv on 2007-09-25
> **jamvegan said:**
> Do the username (amarok) and the password (whatever you made up) match when you ran this:
```
GRANT ALL ON amarok.* TO amarok@localhost IDENTIFIED BY 'PASSWORD_CHANGE_ME';
```
and when you entered the configuration in amarok?

I think, I put the passwork that I put when i ran the code on amarok's mysql configuration. Actually, I accidentally did not change 'PASSWORD_CHANGE_ME' when I ran that so that is also the password that I put on amarok. It's just that, the password I made for mysql is differnent from the one I put in that code and in amarok. Is that okay.

If not, how do I change the passwords that I set already? 

:KS

---

### Post by jamvegan on 2007-09-25
It's fine for the MySQL root password and the amarok@localhost password to be different, in fact, they should be.  It's the amarok@localhost password that you want to use when you're configuring amarok (PASSWORD_CHANGE_ME, in this case).

You can change a password by logging into mysql:
```
mysql -u root -p
```
and then enter the root password when prompted.  Then, if you want to change the root password, type:
```
SET PASSWORD=PASSWORD('new_password');
```
changing new_password to whatever you actually want the password to be.  To change the amarok password, type:
```
SET PASSWORD FOR 'amarok'@'localhost' = PASSWORD('new_password');
```

Hope this helps. :-)

---

### Post by wersdaluv on 2007-09-25
> **jamvegan said:**
> It's fine for the MySQL root password and the amarok@localhost password to be different, in fact, they should be.  It's the amarok@localhost password that you want to use when you're configuring amarok (PASSWORD_CHANGE_ME, in this case).

You can change a password by logging into mysql:
```
mysql -u root -p
```
and then enter the root password when prompted.  Then, if you want to change the root password, type:
```
SET PASSWORD=PASSWORD('new_password');
```
changing new_password to whatever you actually want the password to be.  To change the amarok password, type:
```
SET PASSWORD FOR 'amarok'@'localhost' = PASSWORD('new_password');
```

Hope this helps. :-)

hmmm..
```
~$ mysql -u root -p
Enter password:
ERROR 1045 (28000): Access denied for user 'root'@'localhost' (using password: YES)

```
That error code comes out whenever I enter the password I set for mySQL or amarok. 

What can I do?

---

### Post by jamvegan on 2007-09-26
Hm.  Perhaps the root password is not set?  Try:
```
mysql -u root
```
If that works and you get the mysql prompt (mysql>), then the root password is not set, and you can set it using the command mentioned previously.

If there is a root password, and you don't know what it is, see the MySQL documentation for [How to Reset the Root Password]("http://dev.mysql.com/doc/refman/5.1/en/resetting-permissions.html") (the Linux instructions are below the Windows instructions on the page).

---

