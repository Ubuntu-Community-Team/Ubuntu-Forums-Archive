---
title: "Changing mysql password for a user"
date: 2014-05-25
forum: General Help
---

### Post by nainsurvolte on 2014-05-25
Good day,

I have some issue changing the password of a specific user in mysql.

I start mysql as root and login to the database.

```
mysql -u root -p mythconverg
```

and I send this command

```
mysql> SET PASSWORD FOR 'mythtv'@'localhost' = PASSWORD('mythtv');
Query OK, 0 rows affected (0.00 sec)
```

I also tried without the localhost in it but with no change. The password do not change. 

Any idea on what I am doing wrong or what I should check?

thanks,

---

### Post by Habitual on 2014-05-25
mythtv'@'localhost may actually be something different (like [EMAIL="mythtv@ipa.ddr.ess"]mythtv@ipa.ddr.ess[/EMAIL]) or mythtv@'%'
check the user@host combination with ```
select user, host from mysql.user;
```

---

### Post by nainsurvolte on 2014-05-26
I don`t know why but I tried this one and it worked....

```
[COLOR=#00008B][FONT=Consolas]UPDATE[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] mysql[/FONT][/COLOR][COLOR=#000000][FONT=Consolas].[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]user[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]SET[/FONT][/COLOR][COLOR=#000000][FONT=Consolas] Password[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]PASSWORD[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]([/FONT][/COLOR][COLOR=#800000][FONT=Consolas]'[password]'[/FONT][/COLOR][COLOR=#000000][FONT=Consolas])[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]WHERE[/FONT][/COLOR][COLOR=#00008B][FONT=Consolas]User[/FONT][/COLOR][COLOR=#000000][FONT=Consolas]=[/FONT][/COLOR][COLOR=#800000][FONT=Consolas]'[username]'[/FONT][/COLOR][COLOR=#000000][FONT=Consolas];[/FONT][/COLOR]
```

Thanks.

---

### Post by Habitual on 2014-05-26
Glad it worked out!

---

