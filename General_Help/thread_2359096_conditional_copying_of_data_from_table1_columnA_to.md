---
title: "conditional copying of data from table1 columnA to table2 columnB in MySQL database"
date: 2017-04-20
forum: General Help
---

### Post by yanvolking2 on 2017-04-20
Table 1 below holds account names:

         [TABLE]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]**TABLE 1**[/TD]
[TD="align: center"][/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"][/TD]
[TD="align: center"][/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, colspan: 3, align: center"]**Account Name**
[/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, align: center"]**old **[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**new  **[/TD]
[TD="bgcolor: #B2B2B2, align: center"][/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, align: center"]**account**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**account**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**account**[/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, align: center"]**ID**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**ID**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**name**[/TD]
[/TR]
[TR]
[TD="align: center"]123abc[/TD]
[TD="align: center"]1[/TD]
[TD="align: center"]ACME[/TD]
[/TR]
[TR]
[TD="align: center"]123def[/TD]
[TD="align: center"]2[/TD]
[TD="align: center"]General Motors[/TD]
[/TR]
[TR]
[TD="align: center"]123ghi[/TD]
[TD="align: center"]3[/TD]
[TD="align: center"]Exxon[/TD]
[/TR]
[TR]
[TD="align: center"]123jkl[/TD]
[TD="align: center"]4[/TD]
[TD="align: center"]Microsoft[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]Boeing
[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]6[/TD]
[TD="align: center"]Alphabet[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]7[/TD]
[TD="align: center"]Unilever[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]8[/TD]
[TD="align: center"]AkzoNobel[/TD]
[/TR]
[/TABLE]

There are 2 ID columns because initially the table was created and grown in a database with an alpha-numeric ID generator.  I then migrated the database to MySQL where I was not able to duplicated the original ID generation system.  So all the new accounts entered in the table after being migrated to MySQL needed a new ID column capable of working with MySQL.  I created the new ID column with INT values and with autoincrement, so a new ID value was given right from the first entry (including the entries created in the old database with their existing old account IDs) starting with Nr. 1.  So all the account entries created in the old database and exported to the MySQL database have 2 IDs : the old database ID they were given when created in the old database, AND the new ID given in the MySQL database.  The account entries created in the MySQL database only have the new ID.




Table 2 below holds business project titles relating to their respective accounts by Account ID :

         [TABLE]
[TR]
[TD="align: left"][/TD]
[TD="align: center"]**TABLE 2**[/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="align: left"][/TD]
[TD="align: center"][/TD]
[TD="align: left"][/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, colspan: 3, align: center"]**project register**[/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, align: center"]**old **[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**new **[/TD]
[TD="bgcolor: #B2B2B2, align: center"][/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, align: center"]**account**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**account**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**Development **[/TD]
[/TR]
[TR]
[TD="bgcolor: #B2B2B2, align: center"]**ID**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**ID**[/TD]
[TD="bgcolor: #B2B2B2, align: center"]**Project**[/TD]
[/TR]
[TR]
[TD="align: center"]123jkl[/TD]
[TD="align: center"][/TD]
[TD="align: center"]Open Source Operating System[/TD]
[/TR]
[TR]
[TD="align: center"]123abc[/TD]
[TD="align: center"][/TD]
[TD="align: center"]new drill bit design[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]5[/TD]
[TD="align: center"]Mass Market Moon Cruise Rocket[/TD]
[/TR]
[TR]
[TD="align: center"]123ghi
[/TD]
[TD="align: center"][/TD]
[TD="align: center"]AlphaOmega Oil Platform[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]8[/TD]
[TD="align: center"]Moon Rocket Fuel[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]6[/TD]
[TD="align: center"]Moon Surface Googlemaps[/TD]
[/TR]
[TR]
[TD="align: center"][/TD]
[TD="align: center"]7[/TD]
[TD="align: center"]Waterless Soap[/TD]
[/TR]
[TR]
[TD="align: center"]123def[/TD]
[TD="align: center"][/TD]
[TD="align: center"]oval piston development[/TD]
[/TR]
[/TABLE]

Again, the data in table 2 was initially created in the old database.  So the projects entered in  the old database are referred to the accounts' old ID.  But projects entered after the database was migrated to MySQL relating to new accounts also entered after the migration operation refer to their respective accounts though the new ID.

To clean up the database, I would like to get rid of the old account ID column which is redundant in the new MySQL database.  This is easy as all account entries old and new have a NEW account ID number.  

The problem is correctly filling the new account ID column in table 2.  For example project "New Drill Bit Design" belongs to the ACME account, and therefore ID Number 1 should be written to that line in the new account column, 4 for "Open Source Operating System"; 3 for "AlphaOmega Oil Platform" and so on.  

The values above are surrogates for this example's sake.  In reality the database has thousands of entries in each table.  So there are thousands of entries like those in the Development Project column of table 2 above which have a blank cell in the new account ID column.  

These empty cells could be filled with the correct new account ID value manually but this would require hundreds if not thousands of hours of tedious repetitive work.

[COLOR=#ff0000]**The question is this :**[/COLOR] [I][B]What kind of code (SQL or other) could fill in the empty cells in table 2's new account ID column with the correct value in a single operation?
[/B][/I]
 
Many thanks

Yan

---

### Post by oldos2er on 2017-04-20
Which version of Ubuntu are you running?

---

### Post by SeijiSensei on 2017-04-20
I'd give this a try:

```
update table2 set newid=table1.newid where table2.oldid=table1.oldid;
```

Before doing this, make a backup copy of table2:

```

create table table2_backup like table2;
insert into table2_backup select * from table2;

```

All this assumes that table1.oldid and table2.newid have unique values.

I rarely use sequence numbers as IDs because my databases are usually behind a web application.  If the IDs are numeric and sequential and included in a GET URL, it's very easy to expose other users' private information.  Most of the time I'm generating IDs from a PHP script and use MD5 like this:
```
<?php $id=substr(md5(`ps auxf`),8,16); ?>
```
which takes the process list output from ps (using the "long" format), creates its MD5 summary, and extracts the middle sixteen characters.  It's nearly impossible to generate duplicates with this method, and the resulting IDs are pretty much unguessable.

---

### Post by yanvolking2 on 2017-04-21
I'm using Xubuntu 16.04 LTS.

---

### Post by yanvolking2 on 2017-04-21
Hello SeijiSensei

I just did what you suggested but got he following error message :

MySQL said: [[IMG]http://localhost/phpmyadmin/themes/dot.gif[/IMG]]("http://localhost/phpmyadmin/url.php?url=http%3A%2F%2Fdev.mysql.com%2Fdoc%2Frefman%2F5.7%2Fen%2Ferror-messages-server.html") 

 #1054 - Unknown column 'table1.oldid' in 'where clause'

table1.oldid really does exist as there is a table called 'table1' with a column called 'oldid'; but for some reason MySQL does not recognize it in that particular command.

Any hints as to what is going on and what can be done to solve it?

Thanks

---

### Post by SeijiSensei on 2017-04-21
I use PostgreSQL pretty much all the time so I'm not very familiar with MySQL's quirks.  However it appears that MySQL will only let you reference foreign keys if you use the "innodb" engine.  See [http://stackoverflow.com/questions/1928883/mysql-how-to-set-a-column-to-reference-columns-from-another-table](http://stackoverflow.com/questions/1928883/mysql-how-to-set-a-column-to-reference-columns-from-another-table) for details.  Does that apply to you?

Another possibility is that you may need to JOIN the tables before doing the update.  See [http://stackoverflow.com/questions/11709043/mysql-update-column-with-value-from-another-table](http://stackoverflow.com/questions/11709043/mysql-update-column-with-value-from-another-table).

---

### Post by yanvolking2 on 2017-04-22
Hello SeijiSensei,

I checked the status of my tables in the database and they were all already set up under innodb.  So this cannot be the problem.

Joining the tables before the operation may be a way to solve the problem.  I know about the principles of JOINS in MySQL database management, but I'll have to learn a bit about the code for this, so it may take a little time.

I'll give you some feedback as soon as I master the JOIN commands

Thanks

---

### Post by The Cog on 2017-04-22
How about:
CREATE TABLE table2_new AS SELECT table1.oldid, table1.newid, table2.project FROM table1 JOIN table2 ON table1.oldid=table2.oldid OR table1.newid=table2.newid;
ALTER TABLE table2 RENAME TO table2_old;
ALTER TABLE table2_new RENAME TO table2;


P.S. I trite it on sqlite3 as I don't have access to a MySQL right now.

---

### Post by yanvolking2 on 2017-04-30
Hello There,

I have solved the problem.  In the end SeijiSensei's idea about using a JOIN command was the way.

Here is the code that worked:

```

UPDATE Table2

JOIN Table1
    ON Table2.oldaccountid=Table1.oldaccountid
SET Table2.newaccountid=Table1.newaccountid

```

Thanks to all for your help.


Yan

PS.
I want to mark this post as solved but cannot find the button that enables this

---

