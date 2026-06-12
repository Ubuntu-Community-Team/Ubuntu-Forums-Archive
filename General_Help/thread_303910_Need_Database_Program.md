---
title: "Need Database Program"
date: 2006-11-21
forum: General Help
---

### Post by [pl]ice on 2006-11-21
hi, 
  i need to setup a db , qui all, so that the server can sit on linux and the querry can be used on windows boxes, i don't have experience in db etc. pls advise which program to look into.
thanks!!!

---

### Post by adamkane on 2006-11-21
This will get you started.

Install LAMP (Linux + Apache2 + MySQL + PHP), then acess MySQL database from phpmyadmin webpage from Ubuntu or Windows.

Apache2/PHP4/MySQL4:
```

sudo apt-get install apache2 php4 mysql-client mysql-server phpmyadmin libapache2-mod-php4 libapache2-mod-auth-mysql php4-mysql

```Apache2/PHP5/MySQL4:
```

sudo apt-get install apache2 php5 mysql-client mysql-server phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Apache2/PHP5/MySQL5:
```

sudo apt-get install apache2 php5 mysql-client-5.0 mysql-server-5.0 phpmyadmin libapache2-mod-php5 libapache2-mod-auth-mysql php5-mysql

```Reboot (or start mysql manually).

Open phpmyadmin:
[http://localhost/phpmyadmin](http://localhost/phpmyadmin)

Name: root
Pass: [blank]

---

### Post by [pl]ice on 2006-11-21
ok, but is it hard to get compose a database? what i really need it is like:
-counter timers (for system expiry updates calibrations etc)
-pictures of the instruments , which job they're are, whos on the job etc
-lots of serial numbers etc, 

would it be hard? should i look for intro to SQL and PHP, or just SQL, database wise.
thanks, its really important, if i manage then i can drop a linux box in the office...
thanks

---

### Post by adamkane on 2006-11-21
Pretty simple.

The phpmyadmin interface is the best for new (and experienced) users in my opinion.

In phpmyadmin, you create a sample database. Then create some tables. Then create some fields. Then backup your database every so often.

You then create a PHP page that connects to your database. The PHP page access, and change the data in the database. It can be simple or fancy.

A simpler option may be OpenOffice Base. This is similar to Microsoft Access. I think phpmyadmin is more interesting and fun, but OpenOffice Base may be more your speed. Base will create a file you can save and work on later.

Base is the same. You create a database, then some tables, then some fields in each table. Although you'll probably only need/want one table.

---

### Post by indytim on 2006-11-21
I agree that the LAMP route is a very good choice IF you are willing to devote the time to get up to speed on programming in PHP.  If not, you may want to continue your quest.

Good Luck,

IndyTim

---

### Post by [pl]ice on 2006-11-21
how much PHP do i need? possible that i guess i can put some scripts together etc for it. but yeh will try, it's for a small company but huge ammount of instruments/ cash flow, so it's not easy...

 Any links to good offline PHP tutorials? (pdf etc) i will have a look for books etc.


thanks

---

### Post by adamkane on 2006-11-21
Take a look at OpenOffice Base, and see if it will do what you need.

---

