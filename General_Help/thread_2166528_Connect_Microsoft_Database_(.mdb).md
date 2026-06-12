---
title: "Connect Microsoft Database (.mdb)"
date: 2013-08-09
forum: General Help
---

### Post by lindy2 on 2013-08-09
Libre Office Calc - I'm stuck trying to connect to a Microsoft database. The .mdb database is located in my documents folder. I tried using the url - file:///home/linda/documents/aerosafe.mdb and class path /home/linda but can't connect. I'm new to ubuntu and deciding if we want to repurpose our hardware and start over with ubuntu. Thx.

---

### Post by QIII on 2013-08-09
Microsoft Access will not run in Linux.  The .mdb cannot be instantiated or executed where it is the way you are trying.

You might try running it using Wine, but you would have to install Access and it would have to be running when an ODBC connection is created.

Otherwise, the .mdb could be put on a networked Windows machine with Access installed and the ODBC call made from your Linux machine.

Although I have never had occasion to do it, I believe a Windows machine with Access installed could instantiate and execute an .mdb file stored on a Linux server.

---

### Post by lindy2 on 2013-08-09
Thank you. I'm in over my head! I thought since I was able to view the database, that I would be able to connect to it.

---

### Post by oldfred on 2013-08-10
There are a variety of tools to convert the older .mdb databases to text, or sql databases. You may get into the common issue of sql is not always sql and data definitions for fields vary somewhat. And querys almost always seem different unless very basic.

This is now old but I think still correct.
[http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/](http://blog.moybella.net/2007/03/10/converting-microsoft-access-mdb-into-csv-or-mysql-in-linux/)

You also only convert data, not forms nor reports.

---

