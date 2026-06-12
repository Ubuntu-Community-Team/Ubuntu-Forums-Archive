---
title: "MySQL Admin Crashes"
date: 2005-08-15
forum: General Help
---

### Post by locque on 2005-08-15
For some reason, MySQL administrator crashes when I hit the restore button. It doesn't prompt or anything... Everything else works fine and it does it regardless of which MySQL host I am connected to. I am not sure if it is a bug with the Linux version of MySQL-admin or what... I have looked at the MySQL logs and it show nothing regarding this event... Any Ideas or has anyone else experienced this?

---

### Post by jvictor on 2005-11-06
For me it crashes if i try to click on users admin tab AMD 64

---

### Post by jimbo2150 on 2006-05-15
Mine crashes on user tab too, but everything else seems to work fine. Anyone know what the prob is?

Dapper Flight 7
MySQL Admin (1.1.6-1 build1) (admin-common is installed too)
MySQL server,client 5.0.21-3

---

### Post by danrooke on 2006-05-23
Having same problem with the users tab of MySQL Administrator :neutral:

---

### Post by otis_u on 2006-06-08
I'm also freezing after the users button is pressed.

---

### Post by adamkane on 2006-06-09
Mysqladmin is a PITA. Use phpmyadmin instead:

Apache2/PHP4/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```

Apache2/PHP5/MySQL4 (breezy or dapper):
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Apache2/PHP5/MySQL5 (dapper):
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```

Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by habtish on 2006-06-16
I am having the same problem of mysql freezing when the users tab is hit. I installed phpmyadmin but after the first connection I get an error from phpmyadmin :#2002 - The server is not responding (or the local MySQL server's socket is not correctly configured)
any suggestions?

---

### Post by Codeboi on 2006-07-13
I just had a look at the MySQL site and they have logged this issue as a bug (I'm having the same problem).  

[http://bugs.mysql.com/bug.php?id=20385](http://bugs.mysql.com/bug.php?id=20385)

I guess I'll just throw their admin client in the trash until they fix it.  Wouldn't be the first time I've given up on their client tools, sad.

---

### Post by menaar on 2006-07-13
try Sqlyog. Someone on the forums recommended it to me not long age, and I've been using it regularly.

You need to install it with wine.

You might need to download a dll file also.

[http://www.dll-files.com/dllindex/download.php?gdiplusdownload0UHdXEbMhP](http://www.dll-files.com/dllindex/download.php?gdiplusdownload0UHdXEbMhP)

That's the dll file you need.

put that in /.wine/drive_c/windows/system32/

Install the program from the command line and you shouldn't get any errors.

SqlYog has a very nice user GUI.

Heres the link for sqlyog
[http://www.webyog.com/sqlyog/download_sqlyogfree.html](http://www.webyog.com/sqlyog/download_sqlyogfree.html)

---

