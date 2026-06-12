---
title: "database program that opens sql databases?"
date: 2015-05-18
forum: General Help
---

### Post by mattig89ch on 2015-05-18
hidy ho all,

I was curious if there was a program that allowed you to open and edit an sql database?

I ask because I wanted to try to run windows program in wine, but it needs access to a local sql database

---

### Post by Habitual on 2015-05-18
Access to a local db is [**granted**]("https://dev.mysql.com/doc/refman/5.1/en/grant.html") in the mysql privileges using something like this:
mysql > grant all  on <db>.* to 'user'@'host' identified by 'password';

See [https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql](https://www.digitalocean.com/community/tutorials/how-to-create-a-new-user-and-grant-permissions-in-mysql)

You don't need a program to do this. ;)

---

### Post by mattig89ch on 2015-05-18
I hate to say it, but I do need a program to run an sql database in this case.  The windows program will need to be able to open, edit, and save the database.  its made to do it via sqlexpress.

---

### Post by Habitual on 2015-05-18
Quest_Toad-for-MySQL-Freeware_67.exe
without access being granted, installing it won't do anything for you.

---

### Post by SeijiSensei on 2015-05-18
Why would you think the OP is looking to connect to a MySQL database?  From looking up "[sqlexpress]("https://www.google.com/search?q=sqlexpress")" it's likely to be a Microsoft SQL database.

OP, if you really need to do this on a regular basis like for work, you'll probably be more successful installing [VirtualBox](https://www.virtualbox.org) and creating a virtual machine that runs Windows.

You could try using LibreOffice Base with an ODBC or JDBC connection to the MS SQL database, but that's a lot of hassle and complexity.

---

### Post by mattig89ch on 2015-05-20
Many thanks for that.

I was hoping to have this in my back pocket as a backup.  In case I ever had a client that couldn't afford a windows license.

btw, who are what is OP?

---

### Post by Mopar1973Man on 2015-05-20
There is always MySQL Workbench.
[http://www.mysql.com/products/workbench/](http://www.mysql.com/products/workbench/)

---

### Post by mattig89ch on 2015-05-20
Would that work with a windows program running inside of WINE?

---

### Post by QIII on 2015-05-20
In general internet forum parlance, OP means either Original Poster (in this case, you) or Original Post (the first post in a thread).

---

### Post by mattig89ch on 2015-05-20
Oh I see, danke.

now to experiment to see if I can get this program to recognize a database on my sql workbench

---

### Post by mattig89ch on 2015-05-22
Ok, so I'm running into some difficulty.  Whenever I ran the execuable under wine, it would say something like 'the installer was inturrupted during the setup process and closed.  no changes were made to your system'.

I was trying to run it under the cli, but I'm getting the error wine: /home/username/.wine is not owned by you.  But the ownership properties in the GUI are saying the owner is "Me".

Is there a trick to this I'm missing?

Edit: so I just issued the "sudo chown -R user /home/user/.wine" command.  it didn't give me any errors, but I'm still getting that same error of not owning the folder.

---

### Post by Habitual on 2015-05-22
Matt:
Hopefully, you are not trying to run Quest_Toad-for-MySQL-Freeware_67.exe ?
This may not work in a .wine environment, and it certainly will not work to connect to any sqlexpress database.
Sorry, I shouldn't have recommended that download.

---

### Post by mattig89ch on 2015-05-22
oh, I'm not trying to install the windows version of mysql.  There is one in the software installer, I installed that one, though I haven't done anything with it yet.

No, this is an RMS system we have.  It acts like a register for our clients.  First, I need to run the program, second I need to setup the database (in this case, the practice database), third I need to get the program to read/write to the database.

I'm hitting a bit of an obstacle in the first step though.  As I can't seem to get it to install.

---

