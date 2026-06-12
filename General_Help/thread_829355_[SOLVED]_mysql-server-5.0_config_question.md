---
title: "[SOLVED] mysql-server-5.0 config question"
date: 2008-06-14
forum: General Help
---

### Post by greenstar on 2008-06-14
I am installing some packages one of which required installation of mysql-server-5.0. This wouldn't normally be a problem, except that mysql started asking questions that I don't know how to answer. Googling the net & searching the forums gave me no help.

```
 While not mandatory, it is highly recommended that you set a password for the MySQL administrative "root" user.

If that field is left blank, the password will not be changed.

New password for the MySQL "root" user:
```Keep in mind that all of these questions are as it applies to the mysql-server-5.0 installation only. I have a fair understanding of the system-wide user accounts reasoning.

1. Does this mean that if I don't specify a root password that the root password will be blank or will it be left with some default password?

2. What about security and the root account? Is a blank root password safe?

3. Will it matter?

4. Why not a regular user account?

5. How does the root/sudo debate play into this?

Lost,
Greenstar

---

### Post by HalPomeranz on 2008-06-14
First understand that the MySQL "root" account is distinct from the system "root" account (so the Ubuntu su vs. sudo debate doesn't really apply here).  You connect to MySQL with this "root" account with a command like "mysql -u root -p", which means "connect to MySQL as the MySQL "root" user ("-u root") and prompt me for the password interactively ("-p").  You can run this command as a normal user, you don't need to use sudo to connect to MySQL as the MySQL "root" user.

By default, the MySQL "root" account has all privileges on all databases on your system.  Thus it can add/drop databases, create/delete tables within databases, modify any data, plus do specific administrative tasks like adding additional users and granting them different privilege levels.  You could create a different account that had these privileges if you wanted to, but the "root" name is more or less standard.

Should you have a password on this account?  I'd say "definitely yes", especially if you plan on allowing access to your databases from remote systems.

For more information, see the Chapter 5 of the MySQL manual:

[http://dev.mysql.com/doc/refman/5.0/en/server-administration.html](http://dev.mysql.com/doc/refman/5.0/en/server-administration.html)

---

### Post by kalesh7 on 2008-06-14
1) I think it will remain blank

2)generally speaking a blank password is never safe, but then what data will you store in the database? is the data sensitive? private? or could you not care less about the data? if the data is sensitive then a very strong root password is a must, however if the data is just some random stuff(example the database I use for development does not have any real data on development machine so I can get away with weak password) then password doesn't matter. Note this does not affect your normal root/ user accounts and is only used for mysql

3) see 2

4) because mysql accounts are fundamentally different then your user accounts (and you need a root account to create normal user accounts on mysql) so later you could create a normal user account and use that.

5) it doesn't, see above.

---

### Post by greenstar on 2008-06-15
Thanks to both responders for the detailed answers. I appreciate the clarification and now know how to proceed. FYI, I was installing zoneminder. Since I may wish to access it remotely at some point, I used a password.

Thanks for your time & assistance.

Greenstar

---

