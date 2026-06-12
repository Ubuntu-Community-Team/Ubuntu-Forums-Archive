---
title: "SQL server manager equivalent for Linux/Ubuntu?"
date: 2007-02-12
forum: General Help
---

### Post by swappa on 2007-02-12
**Hello**

I'm a Linux/Ubuntu semi newbie (been using it seriously for a year or so..) and I'm looking to make the permanent move from XP to Ubuntu. I am 98% there, I just need to find some utils  that I cant do without since they are major components in my every day work situation. One of those programs are SQL Server enterprise manager/Management studio. Anyone know if there are such tools for Linux?
Vmware could very well be the solution but I am having a little bit of challenge making it work 100%, so right now I'm in a dual boot situation. Thats ok, but not really what I want. 

Thanks. 


:D

---

### Post by der_joachim on 2007-02-12
There are database servers available for linux, which have their own GUIs. The most popular database server is MySQL and its administrator tool. The MySQL query analyzer is quite similar to the MSSQL query analyzer. 

If you want to be able to connect to a MSSQL server, you'll probably want to configure an ODBC driver. Try installing the unixodbc and freetds drivers. You'll probably have to enable the universe repository. 

I'd post some config files, but I am not at work now.

Good luck.

---

### Post by seppo on 2007-02-12
Personally I'm a fan of the SQuirrel SQL client:

[http://squirrel-sql.sourceforge.net/](http://squirrel-sql.sourceforge.net/)

It is written in Java and is very modular by design. It supports MySQL, MSSQL and Oracle JDBC perfectly.

---

### Post by swappa on 2007-02-12
Thanks for responding. I'll check out the squirrel sql client option :)

---

### Post by Pathan on 2007-06-03
Hi,
I have downloaded the SquirrelSQl client's jar files but I am unable to install it. Can anybody help?

---

