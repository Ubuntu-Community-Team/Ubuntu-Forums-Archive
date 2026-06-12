---
title: "sql-ledger, apache2, apache &amp; perl problems"
date: 2005-10-03
forum: General Help
---

### Post by keninman on 2005-10-03
I have installed Ubuntu 5.10 clean. I installed sql-ledger and copied it to /var/www/sql-ledger for testing. When trying to access it get a download prompt from firefox for login.pl. I have tried using apache2 but only get a connection refused if I start apache2 and stop apache 1.3.33 *"Sql-ledger package depends on apache 1.3.33?"* Apache2 showed it was installed and running but I could only get connection refused when connecting to [http://localhost](http://localhost) ? Apache 1.3.33 loads the default page fine but will not run any perl scripts. If I try to enable mod_perl.c in webmin I get a syntax error, now since reinstalling mod_perl isn't even there. Could something here be the problem?

I have beat myself silly searching forums and trying different things. I have deleted and installed Ubuntu twice with no success. I really only need this thing to run as a server and handle sql-ledger. I am new to Ubuntu but have ran Mandrake for years, I am no guru but I can get around Linux okay. I see others here have sql-ledger running and was hoping maybe someone could help me get it going.

Thanks in advance,
Ken Inman

---

### Post by Tinwood on 2005-10-06
[quote=keninman]I have installed Ubuntu 5.10 clean. I installed sql-ledger and copied it to /var/www/sql-ledger for testing. When trying to access it get a download prompt from firefox for login.pl. I have tried using apache2 but only get a connection refused if I start apache2 and stop apache 1.3.33 *"Sql-ledger package depends on apache 1.3.33?"* Apache2 showed it was installed and running but I could only get connection refused when connecting to [http://localhost]("http://localhost") ? Apache 1.3.33 loads the default page fine but will not run any perl scripts. If I try to enable mod_perl.c in webmin I get a syntax error, now since reinstalling mod_perl isn't even there. Could something here be the problem?

I have beat myself silly searching forums and trying different things. I have deleted and installed Ubuntu twice with no success. I really only need this thing to run as a server and handle sql-ledger. I am new to Ubuntu but have ran Mandrake for years, I am no guru but I can get around Linux okay. I see others here have sql-ledger running and was hoping maybe someone could help me get it going.

Thanks in advance,
Ken Inman[/quote] 
Firstly, you don't need mod_perl so just the plain vanilla apache or apache2 is all that is required; it runs through CGI scripts.

Have you actually configured the web-server to serve it?  i.e in the README instructions it says:

```
create a file sql-ledger-httpd.conf in the same location
 where your httpd.conf is and copy the next section into the file
 
   Alias /sql-ledger /usr/local/sql-ledger/
   <Directory /usr/local/sql-ledger>
     AllowOverride All
     AddHandler cgi-script .pl
     AddDefaultCharset On
     Options ExecCGI Includes FollowSymlinks
     Order Allow,Deny
     Allow from All
   </Directory>
 
   <Directory /usr/local/sql-ledger/users>
     Order Deny,Allow
     Deny from All
   </Directory>
 
 edit httpd.conf and add
 
   # SQL-Ledger
   Include /config_directory/sql-ledger-httpd.conf
``` You'll need to change /usr/local/sql-ledger and /usr/local/sql-ledger/users to where you have put it (/var/www/sql-ledger).

-- 
Alex.

---

### Post by keninman on 2005-10-11
Sorry I took so long to reply. I have been busy setting up SQL-Ledger at my business and getting it installed for more testing on my home system. 

I had zero luck using the synaptics manager to install SQL-Ledger. I had more luck using the setup.pl from [sql-ledger.org]("http://www.sql-ledger.org"). There are just so many dependencies and tweaks needed to get it working. I had the most trouble with Postgresql. I ended up using Postgresql 7.4 in my business and 8.0 on my home system. 

Getting it running is one thing. Setting it up is another, especially if you are not an accountant. The learning has been tough going but I love the flexability. SQL-Ledger is the best program I have found, even better than most of the “store bought” offerings. My business is small and still struggling but it was time to move away from spreadsheets to an accounting program that allows me to manage inventory and customers easier. I just could not afford to purchase Quickbooks or Peachtree and the lower cost offerings just could not fulfill my needs. I also love the fact that I can access my accounting from any computer in the building. I also print to a network printer and it is very easy to use the print feature in Firefox by sending the print job to the screen instead of printing from SQL-Ledger which is very limiting on what printers you can use. The only thing I have found lacking is drop down menus for putting good or services in an invoice, quote or POS sale.

I wish Ubuntu's package manager did a better job of installing SQL-Ledger, perhaps someone more skilled than I could write a new package that takes care of Apache2, Postgresql-8.0 and handles the setup better than the existing one or at least write a comprehensive how to. To sum up though it is well worth the trouble to get SQL-Ledger running and learning how to use it.

---

### Post by imri303 on 2008-03-31
I am running Ubuntu Gutsy. I have installed all packages required Apache2, postgresql, various perl packages... I followed the install instructions and when I try to get to the admin.pl page firefox tries to download it. I have tried putting sql-ledger-httpd.conf in conf.d, using an include statement in apache2.conf, and just plain pasting the directory section directly into apache2.conf. Anyone have any ideas? BTW I can get to the login page which is a pl file as well which is why this seems so weird. Why would it run one but not the other? The permissions on the files are exactly the same and they are both owned by root:root.

---

### Post by Tinwood on 2008-04-01
If your browser attempts to download a .pl script then the problem is that Apache doesn't know it is a script.  You don't mention whether you are using mod_perl or running sql-ledger as a CGI script.  Note, I'd use [http://www.ledgersmb.org/](http://www.ledgersmb.org/) as it is a community derived fork SQL Ledger that seems to be making more progress.  I run LedgerSMB

Anyway, if you a running SQL Ledger as a CGI then you need:

```
AddHandler cgi-script .pl
```in your apache configuration.  Also, you will need a

```
Options +ExecCGI
```for the root folder of your sql-ledger installation.  e.g. if you were using a virtual host to run it, something like:

```


<VirtualHost *:80>
    ServerAdmin  mail@example.com
    DocumentRoot /home/sql-ledger
    ServerName   sql-ledger.example.com
    ErrorLog     /var/log/sql-ledger/error.log
    CustomLog    /var/log/sql-ledger/common2.log common
    AddHandler cgi-script .pl

    <Location "/">
        Options    +ExecCGI -Indexes
    </Location>

</VirtualHost>

```Obviously, if you're not using a virtual host then you just need the AddHandler and Options lines, plus maybe an Alias to link a subdirectory to where the sql-ledger instance is installed.

HTH
Alex.

---

