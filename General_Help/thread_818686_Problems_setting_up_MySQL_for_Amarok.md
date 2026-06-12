---
title: "Problems setting up MySQL for Amarok"
date: 2008-06-04
forum: General Help
---

### Post by Stef@n on 2008-06-04
Hi guys,

A couple of days ago I tried setting up MySQL for Amarok using this guide:

[http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html](http://mikesubuntu.blogspot.com/2007/09/how-to-set-up-mysql-database-in-amarok.html)

This always worked flawless in the past, but now i've seemed to screw things up and I don't know what. I keep getting this error message:

*Access denied for user 'root'@'localhost'*

Since i'm a MySQL-n00b I've tried searching the net for a sollution, but I can't seem to find one. The only sensible solution I could think of was uninstalling the server + client and reinstall. But that didn't help.

Can anyone guide me through this?

Thanks in advance!

---

### Post by Stef@n on 2008-06-05
Can anyone please help me? I have a huge music collection and sqllite is way to slow. Let me know if I need to supply more information...

---

### Post by Nepherte on 2008-06-05
There's a much easier solution. Assuming you have installed mysql, you can get all that by going to settings > configure > collection in the amarok menu. Then choose mysql as database. You fill in the hostname (localhost), *a database name* (I suggest you use something different than the one in the guide you followed), user name and password.

The error suggests some permissions error though. I believe you are using the wrong user name. You try to access the amarok database with root while you should use amarok which you granted all rights on the amarok database identified by the password you specified. So try amarok with the password you specified and see if that works.

---

### Post by Stef@n on 2008-06-05
Thanks Nepherte for your response!

I tried setting up a database with a different name, password, etc. following the guide from my first post (I hope this is what you meant). Like this:

[I]mysql> CREATE DATABASE eodm
-> USE mysql
-> GRANT ALL ON eodm.* TO eodm@localhost IDENTIFIED BY 'eodm' 
-> FLUSH PRIVILEGES
-> \q
Bye[/I]

But no matter what I try I get the following message:

[I]MySQL reported the following error:
Access denied for user 'eodm'@'localhost' (using password: YES)[/I]

Maybe I set the password (with the first command from the guide: *mysqladmin -u root password PASSWORD*) to one I can't remember. Is there a way to reset this?

---

