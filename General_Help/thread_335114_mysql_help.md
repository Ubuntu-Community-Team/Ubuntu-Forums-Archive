---
title: "mysql help"
date: 2007-01-09
forum: General Help
---

### Post by notatoad on 2007-01-09
i installed apache2, php5, and mysql following the ubuntuguide wiki.  when i get to the step where i have to set a password for mysql, i get this error:

```
kyle@bender:~$ mysqladmin -u root password *******
mysqladmin: connect to server at 'localhost' failed
error: 'Access denied for user 'root'@'localhost' (using password: NO)'
```
where ******** is my password in plain text

anybody know what's happening?  i can't tell if it is just saying that it can't connect to mysql, or if root already has a password

---

### Post by johnwillis on 2007-01-09
Try this dude.

It works when I use it.

```
shell> mysql -u root
mysql> SET PASSWORD FOR ''@'localhost' = PASSWORD('newpwd');
```

just insert your new password into the 'newpwd' bit.

Hope this helps.

- JW

---

### Post by bcnaat on 2007-01-14
at the prompt type:
```

mysql -u root -p password

```

password being your password.

If you don't want anyone to see your password when you're typing it in then use this code:

```

mysql -u root -p

```

It will then prompt you for the root password and it won't show when you type it. All you were missing was the -p for password prompting or usage. This is why it gave you the message "(using password: NO)"

Hope this helps.

Kay

---

