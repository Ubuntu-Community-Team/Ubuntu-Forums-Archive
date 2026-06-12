---
title: "Problems with sql-ledger"
date: 2005-08-30
forum: General Help
---

### Post by torjusg on 2005-08-30
I am trying to set up sql-ledger for my one man company, but I can not access the [http://localhost/sql-ledger/admin.pl](http://localhost/sql-ledger/admin.pl) page. I have followed the instructions in the documentation, but invariably get this message:
"
Not Found

The requested URL /sql-ledger/admin.pl was not found on this server.
Apache/2.0.53 (Ubuntu) Server at localhost Port 80
"

Does any of you know what is wrong?
Do I have to edit any files?

Torjus Gaaren

PS! If you have seen this message before, it is because I posted this one in the wrong forum the first time.

---

### Post by d1337 on 2005-08-30
I have been using sql-ledger since January of this year to run my business.  You are probably better off posting to the sql-ledger mailing list or searching the archives on source forge as sql-ledger is rather specialized in permissions, how it ties itself to postgresql, etc.  While I can't offer you a solution, it sounds to me as if your database is either not created or your permissions are not set correctly.  The community of sql-ledger users is quite helpful to support/troubleshoot that package, but again it is a bit different than what I think this forum means by Other App Support because of it's nature.  If you would like some links to where you may look, I'll subscribe to this thread and shoot them to you this evening.

d1337

---

### Post by torjusg on 2005-09-01
I fixed this problem, to other people struggeling with the mentioned problem:

Ubuntu puts the file sql-ledger-httpd.conf in /etc/sql-ledger. 

By adding:

# SQL-Ledger
Include /etc/sql-ledger/sql-ledger-httpd.conf

to the file /etc/apache2/apache2.conf

and restarting apache with the command:

sudo apache2ctl restart

you will find the starting page.

Torjus Gaaren

---

### Post by torjusg on 2005-09-01
That brings me to the next question:

When I try to create a dataset it returns:

Error!

FATAL: IDENT authentication failed for user "sql-ledger"

The faq tells me to edit /etc/postgresql/pg_hba.conf, but if I do, the create dataset returns that there is an error in this file.

Does anyone know how I edit this file so that it works?

The faq is found here: 
[http://www.sql-ledger.com/cgi-bin/nav.pl?page=misc/faq.html&title=FAQ](http://www.sql-ledger.com/cgi-bin/nav.pl?page=misc/faq.html&title=FAQ)

The readme is found here:
[http://www.sql-ledger.com/cgi-bin/nav.pl?page=source/readme.txt&title=README](http://www.sql-ledger.com/cgi-bin/nav.pl?page=source/readme.txt&title=README)

Torjus Gaaren

---

### Post by torjusg on 2005-09-02
Ok, fixed that problem too. :grin: 

It now works after I removed the # in front of the line saying:

local        all           all           trust

in the file /var/lib/postgres/data/pg_hba.conf

Remember to reboot

Torjus Gaaren

---

### Post by tenoca on 2006-02-20
First of all,
Thank you.
including:
Include /etc/sql-ledger/sql-ledger-httpd.conf & restarting apache works great, but How do I login?
ok, I got this, clicked on the administrator admin, at the bottom, next question>>>>
How do I configure this? how do I create setup/create a database for this?

---

