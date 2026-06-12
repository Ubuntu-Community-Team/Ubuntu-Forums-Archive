---
title: "Management software"
date: 2017-07-14
forum: General Help
---

### Post by 4l3x2 on 2017-07-14
Hi all.
I didn't figure where this topic could be put, of course it can be moved if needed.

I need to know if is there an open source software which can help the management of a given database of articles in terms of getting informations about sales, revenue etc...

I'll try to explain better:
I manufacture a product and I don't sell it directly, but I give it to a V.A.R. (Value Added Reseller), which sells it on the market and, periodically, gives me back my profit, accompanied by detailed documents.
When needed I want to know a detailed situation, for example, every week I want to query the database and ask, from a given date until another, how many units I've sold, when, to whom, how much I've earned etc...
The data in the database can be put manually (ie: by a trained monkey reading the documents from the VAR) or automatically, if the software can read the data from a .csv or a .xls or whatever file type or external database structured in a given way.

For now we are using 2+1 types of database:
1. Oracle
2. PostGreSql
 .
 .
 .
+1. Access (:oops:)
Don't laugh please.....

Since our production softwares will rely on PostGreSql only, in a very near future, I do prefer if this software will be able to interface with it, maybe even allowing us to create and manage an instance.

If I wasn't clear try to ask, I'll try to answer the best way I can.

Thank you very much :)

---

### Post by SeijiSensei on 2017-07-14
Do you use Access with the PostgreSQL ODBC connector, or just maintain a native Access databases?

If you add the connectors for Oracle and PostgreSQL, you should be able to build an Access database that incorporates the data from all three sources to produce the kinds of reports you need.

I wouldn't laugh at you for using Access at all.  I use PostgreSQL for all my database applications, usually with the command-line client.  However Access provides a more convenient front-end for tasks like uploading data into PG.  For instance, you can import an xls/csv file, then run an Append query to add the data to existing PG tables.  I also find Access a very helpful client if I need to construct complex relational queries across multiple tables.

---

### Post by 4l3x2 on 2017-07-15
Our databases are completely unconnected, PG contains raw data from sensors, a workgroup evaluates raw data and builds plain files which are used by a second workgroup to insert examinated data in the Oracle database, where are located the final products too (the products are built by 2 workgroups).
Since both the software used to evaluate data from the sensor and build  the products are from the same software house, they want to modify the  latter to use PG.

In addition we have a plethora of little old Access databases (with no documentation, obviously....) which were built to allow the managers doing their bullshits, for example:
- keep note in a human readable form of the updates of the product
- build graphics of the work percentage on a single product (pie chart, histograms....)
- print reports of the status of the products, altogether or divided by some criterion

All Access databases are manually updated.
As a result I spend 90% of my time maintaining their little Access programs, instead of doing my work.

Obviously if I ask to attend some kind of course of Oracle/PG/Access, programming or anything else my boss answers no, I'm attending university (Information Science) at my expense because I have the passion.

The data like the information on the selling, decrees on the validity of a single product or entry into force of the same etc.... are mostly in the paper form and come from different sources, so every time a manager needs to rebuild the history of a product he has to ask to several people, so the idea is to make a software which takes in input all these informations and automatically retrieve them from a database.

My idea was to use PG and an open source client to do the task, so the users can do some tasks by their own without bothering me ("I want to add a column in which storing how many times an employee goes into the bathroom", "I want to put a button in the secondary mask to visualize this graphic") and, possibly, in the time they can move all their little programs in it.
 I don't want to build another Access program to maintain....

---

### Post by dragonfly41 on 2017-07-15
[COLOR=#000000]> Since our production softwares will rely on PostGreSql only, in a very near future, I do prefer if this software will be able to interface with it, maybe even allowing us to create and manage an instance.

From your description it seems that one path is to migrate all Access apps to use PostgreSQL.

Personally I don't use Access or PostgreSQL but I suggest that you explore a front end framework like jqwidgets running on a tomcat server on Ubuntu so that you can use JSP.

Here is an example of binding PostgreSQL to JSP.

[/COLOR][http://www.jqwidgets.com/jquery-widgets-documentation/documentation/java-integration/bind-jquery-grid-to-postgresql-database-using-jsp.htm](http://www.jqwidgets.com/jquery-widgets-documentation/documentation/java-integration/bind-jquery-grid-to-postgresql-database-using-jsp.htm)

Then the task is:

(a) migrating all Access apps to PostgreSQL.

[http://www.olschimke.eu/2012/08/07/importing-microsoft-access-mdb-into-postgresql-on-linux-postgres/](http://www.olschimke.eu/2012/08/07/importing-microsoft-access-mdb-into-postgresql-on-linux-postgres/)


(b) using jqwidgets develop front end GUI's for your various user groups.

This approach allows you to consolidate all your various apps on PostgreSQL and support your learning of Information Science.

Longer term you might consider MVC frameworks such as laravel5.   That is another chapter.

...

There is this tool for managing databases.

[http://www.razorsql.com/index.html](http://www.razorsql.com/index.html)

It is not free but weigh the costs of your administration time and costs of dependency on external systems house.

Alternatives are here ...

[http://alternativeto.net/software/razorsql/](http://alternativeto.net/software/razorsql/)

---

### Post by SeijiSensei on 2017-07-15
Another option is to use PHP on a web server to create the front end.  PHP has built-in PostgreSQL functions.

---

### Post by dragonfly41 on 2017-07-16
> [COLOR=#000000]Another option is to use PHP on a web server to create the front end. PHP has built-in PostgreSQL functions.
[B]
+1[/B] .. PHP is my preferred choice too for development.   
There are also PHP bindings in jqwidgets framework and installing a LAMP server opens a path to (later) explore applying Laravel5.


[/COLOR]

---

### Post by SeijiSensei on 2017-07-16
Well, in this case it would be a "LAPP" server since the OP is using PostgreSQL :D

I once had an industrial glass manufacturer as a client. As you can imagine, not every piece of glass that leaves the factory arrives at the worksite intact.  So they had an elaborate system of paper forms that they wanted to automate.  The factory ran a custom Oracle application for glass makers on Linux.  I created a PG database for the information about breakages and attached to both it and the Oracle databases with PHP to create forms, reports, etc., accessible from a web browser.

---

### Post by 4l3x2 on 2017-07-17
Wow, I have lots of things to study, thank you very much to all ;)

---

### Post by mastablasta on 2017-07-17
is this all what ERP does. sure one can make one for themselves, fully cusotmized. but there are some open ones like Odoo.

bu still i agree these kin dof tasks shoul dbe digitized and automated. paper order? we removed those. some still send in PDFs but even that will go away soon.

---

