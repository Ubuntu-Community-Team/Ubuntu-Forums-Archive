---
title: "Need alternative for MS SQL server"
date: 2008-05-26
forum: General Help
---

### Post by rakan_dr on 2008-05-26
Hi guys,
I'm a computer science student and now we're learning SQL in the university and we apply what we learned on Microsoft SQL Server 2005, so please guys give me alternative to this software so I can apply the (STANDARD) SQL we learn on it. Please I want it with Visual interface and with a pre-created database like the Northwind in MS SQL Server 2005.

note: Mysql doesn't work for me cuz it's different a little bit.

Regards.

---

### Post by Nepherte on 2008-05-26
Being a computer science student myself, I saw SQL too but apart from some minor differences, it should be pretty much the same for MySQL! Another option is Oracle, dunno if they have a free version though.

---

### Post by rakan_dr on 2008-05-26
> **Nepherte said:**
> Being a computer science student myself, I saw SQL too but apart from some minor differences, it should be pretty much the same for MySQL! Another option is Oracle, dunno if they have a free version though.

Did you use the Mysql?? I used it a little bit, but its queries are different a little bit than MS SQL Server 2005, I want such a program to practice what I've learned in MS SQL Server.

---

### Post by tribaal on 2008-05-26
Unfortunately, MSSQL uses its own superset of the SQL language. So there will be no other database with the exact same command set as MS SQL.

The same goes around the other way - PostgreSQL and MySQL both use their own superset of SQL, like Oracle.

So while *most* of the code should be the same, you will never find something that is 100% the same. 
This has nothing to do with linux however, you'll have the same problem in windows (if you try to use another DB in windows, that is).

My suggestion:

Install VirtualBox or VMware Server on your machine, install windows in a virtual machine and run MS SQL from in there.

You can access everything through the network, so you don't even have to bother with Window's GUI (just boot the VM and away you go).

Hope this helps...

- Trib'

---

### Post by rakan_dr on 2008-05-26
Yeah man I agree with you about the SQL, but anyway I'm learning standard SQL and some times we learn some queries that don't exist in MS SQL.

> **tribaal said:**
> 
My suggestion:

Install VirtualBox or VMware Server on your machine, install windows in a virtual machine and run MS SQL from in there.

You can access everything through the network, so you don't even have to bother with Window's GUI (just boot the VM and away you go).



- Trib'
please man I didn't understand this point. What do you mean by it? How can I write my queries through the network??? 
Can you explain it please?

---

### Post by rakan_dr on 2008-05-27
Does Mysql have a Visual Interface in Ubuntu?

---

### Post by Nepherte on 2008-05-27
There are several tools:
mysql-query-browser gui to query your mysql database
msyql-admin gui for mysql administration

or phpmyadmin is very popular web based system.

Everything mentionned is in the repositories.

---

