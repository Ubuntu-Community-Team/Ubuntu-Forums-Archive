---
title: "OpenOffice 2 Base woes"
date: 2005-04-21
forum: General Help
---

### Post by andvaranaut on 2005-04-21
Hi all,

I'm having trouble getting OpenOffice2 Base to work. I want to create an embedded database (HSQL). I started Openoffice2 and created a new database. OOo complained about not having a Java runtime installed. I tried again after installing sun-j2re from Backports and it seemed to work fine; the database is created and registered. However, whenever I try to do anything with the database (eg. clicking the Tables icon) the following error appears:

The connection to the data source <filename> could not be established. The specified driver could not be loaded!

There is an OK button and a More button. Clicking More reveals an additional error: "Error code -1 org/hsqldb/jdbcDriver"

Furthermore, if I close Base and relaunch OpenOffice, a recover dialog appears to repair the database file. If I click Recover the database file seems to be recovered successfully, but the next time I start OpenOffice the recover dialog returns. Rather annoying.

Has anybody been able to make oo2 base to work? If so, what JRE/database drivers are you using?

Thanks, andvaranaut.

PS: I have unixodbc installed as suggested by the openoffice2 package.

---

### Post by jatos on 2005-11-02
I get the same error problems when I connect to a MySQL database, on Windows and Ubuntu, I could glad for any assistance as well

---

### Post by henriquemaia on 2005-11-06
[QUOTE=jatos]I get the same error problems when I connect to a MySQL database, on Windows and Ubuntu, I could glad for any assistance as well[/QUOTE]

I think you need to do the following:
 
1.Go to [http://dev.mysql.com/downloads/connector/j/3.1.html](http://dev.mysql.com/downloads/connector/j/3.1.html)
2.Download the driver.
3.Unzip it to whatever place you like (e.g ~/.openoffice2/javadriver/)
4.Open OpenOffice2.
5.Inside OO.o, select tools/options/java/class path/add archive
and select the .bin you got from [www.mysql.com](www.mysql.com).
6.Restart OO.o

Now everything should work fine in your connections to mysql, assuming that you have mysql correctly configured.

Best luck

---

