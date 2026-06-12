---
title: "How i can open odbc administrator gui ?"
date: 2015-04-18
forum: General Help
---

### Post by rhandy2 on 2015-04-18
Hello

Im new to ubuntu and linux, I install odbc libraries and gui intarface from ubuntu software center, but now I dont know hoe to start it.

Thanks!!!!

---

### Post by cariboo on 2015-04-18
Moved to General Help, as it seems to have nothing to do with 15.04

---

### Post by SeijiSensei on 2015-04-18
If you are talking about using the ODBC libraries for Linux to connect to an SQL server running on Windows, I'd start here:  [http://www.unixodbc.org/](http://www.unixodbc.org/).  You must have a specific application in mind, yes?  What are you trying to accomplish?

I've only used ODBC to connect from Windows programs like MS Access to SQL servers running PostgreSQL or MySQL on Linux.  I can't help much with connecting the other way round.

---

### Post by rhandy2 on 2015-04-18
Yes I is it!
I start [http://www.unixodbc.org/](http://www.unixodbc.org/) but I cant configure it. I need some help. I have one old database in PARADOX, and I use PHP odbc to connect on windows 2003 server.
I want stop using windows 2003 server, I was thinking  install ubuntu and xampp. Only problem  connect to ODBC  PARADOX.


I use this:
[FONT=Arial][FONT=Arial][FONT=Arial]./configure --prefix=/usr/local/unixODBC                  [/FONT][/FONT][/FONT][FONT=Arial][FONT=Arial][FONT=Arial] --sysconfdir=/etc                  [/FONT][/FONT][/FONT]--enable-gui --enable-drivers --enable-drivers_conf
make
sudo
make install
____________

Now I have  /etc/odbcinst.ini and /etc/odbc.ini files EMPTY

I found this wizard  on  urs/bin/ODBCCreateDataSourceQ4.

After I see this page [https://help.ubuntu.com/community/ODBC](https://help.ubuntu.com/community/ODBC)

I could found MYSQL on wizard.



anyone could help me to configure some like that page?

---

### Post by SeijiSensei on 2015-04-18
If you want to use the native ODBC functions in PHP, install the **php5-odbc** package from the repositories and restart Apache.  

Can you export the Paradox database in some text format?  If there aren't many complex relations, you could dump the database to comma- or tab-separated files and rebuild the database in something like PostgreSQL or MySQL.

---

### Post by rhandy2 on 2015-04-19
Yes I can, but is not the solution, because I use one software everyday in my office and it uses paradox. In php I made one page to load that database and I use it for docs digitalization managment. I need one DSN just like I use in windows to make connect to php odbc.

---

