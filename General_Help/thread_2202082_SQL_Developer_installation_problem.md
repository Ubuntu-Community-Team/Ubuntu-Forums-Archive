---
title: "SQL Developer installation problem"
date: 2014-01-27
forum: General Help
---

### Post by eugen2 on 2014-01-27
[COLOR=#000000][COLOR=#000000]Hi everyone,[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]i have installed on WM Ware following:[/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000]Ubuntu 12.04 LTS 64bit - ok![/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Java JDK 1.7.0.0_51 - ok! (Java 7 Oracle)[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]SQL Developer 4.0.0.13.80-1 - ok![/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Java Path configuration -ok![/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]After installation of SQL Developer i started the SQL Developer and configured the connection. Everything works fine![/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000]But if i close the SQL Developer, i can not start it.[/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000]Please help me, i have spend alot of time with this problem [/COLOR][/COLOR]



[COLOR=#000000][COLOR=#000000]Thanks![/COLOR][/COLOR]

---

### Post by digitaleagle on 2014-01-30
Try unsetting a couple of variables:

```
unset GNOME_DESKTOP_SESSION_ID
unset DBUS_SESSION_BUS_ADDRESS

```
I just added that to the top of the launcher script:
sudo  gedit /usr/bin/sqldeveloper

[IMG]http://linuxsagas.digitaleagle.net/wp-content/uploads/2014/01/Selection_142.png[/IMG]

I kept notes on installing SQL Developer 4.0 on my system on my blog: [http://linuxsagas.digitaleagle.net/2014/01/28/fixing-sql-developer-4-0/](http://linuxsagas.digitaleagle.net/2014/01/28/fixing-sql-developer-4-0/)

---

