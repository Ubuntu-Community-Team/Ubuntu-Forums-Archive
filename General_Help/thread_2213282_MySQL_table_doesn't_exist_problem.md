---
title: "MySQL table doesn't exist problem"
date: 2014-03-25
forum: General Help
---

### Post by jp.brandon on 2014-03-25
First off I am new to Ubuntu and Linux in general. I am a Web Developer and Database Administrator at a online timeshare company. 

The other day my Windows machine that I was doing all my data on with SQLyog, crashed. I was able to save all the .ibd, .myi, .opt, .frm files from the xampp/mysql/data/ folder. I had Ubuntu on the machine as secondary boot so I decided to just start using that for now. I installed Wine and SQLyog onto Ubuntu. After figuring out how to access /var/lib/mysql folder (because of the permission) I was able to copy all my database folders into there. 

When I open up SQLyog I can see each database and the tables within. However when I click to view the table or to try and run a query it pops up with a MySQL Error:

```

Error Number: 1146
Error Message: Table `amg.t1-t2_good` doesn't exist

```

I even tried running the query in the terminal:

```

mysql> use `amg`;
    database changed
mysql> select count(*) from `t1-t2_good`;
    Error 1146 (42s02): Table `amg.t1-t2_good` doesn't exist

```

After some reading I thought it might of been permission still, for the amg database folder I gave it the user mysql and group mysql:

```

chown -R mysql:mysql amg/

```

That didn't fix anything. So I am currently stuck and not exactly sure what to do. Worst case, I would have to start over and input raw data. That would take way too long as I deal with 5+ million records, and don't really want to switch back to Windows.

Any Ideas?!

---

### Post by Habitual on 2014-03-26
backup, Backup, BACKUP!

Does the 'missing' table exist in the Windows mysql instance? if so, export the amg db data from the Windows mysql instance to an .sql file using mysqldump or an equivalent on Windows, copy the file.sql to the Linux host and import it into a newly created amg db on the Linux mysql instance.

On the Linux side you should see the db under /var/lib/mysql/amg and that is where the files you "saved" (from the Windows instance) should go, making the correct permission assignment:
```
chown -R mysql:mysql /var/lib/mysql/amg/
```

To import on the file.sql on the Linux side use:
```
mysql -uroot -p amg < /path/to/file.sql
```

It is NOT a reason to "switch back to Windows" IMO.

Study [http://www.cyberciti.biz/faq/import-mysql-dumpfile-sql-datafile-into-my-database/](http://www.cyberciti.biz/faq/import-mysql-dumpfile-sql-datafile-into-my-database/)
for examples.

Good luck.

---

### Post by jp.brandon on 2014-03-27
After about 20 mins to load the windows login screen and another 10-20 mins to load the desktop. I was able to get into SQLyog and dump the databases. Thank God! I was getting worried for a min lol. Thanks for the help

---

### Post by Habitual on 2014-03-28
You are very welcome.

---

