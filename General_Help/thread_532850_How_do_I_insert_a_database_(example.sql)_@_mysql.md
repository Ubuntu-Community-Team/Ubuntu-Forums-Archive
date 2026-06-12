---
title: "How do I insert a database (example.sql) @ mysql?"
date: 2007-08-23
forum: General Help
---

### Post by benevolent on 2007-08-23
:confused::confused::confused:

---

### Post by _samba_ on 2007-08-23
mysql -p -h SQLSERVER dbname < example.sql

[http://dev.mysql.com/doc/refman/5.0/en/upgrading-to-arch.html](http://dev.mysql.com/doc/refman/5.0/en/upgrading-to-arch.html)

cheers

---

### Post by LaRoza on 2007-08-23
```

mysql -u *UserName* -p *databaseName* < *sqlFile.sql*

```

If you want the results to go into a file, redirect the output with >, so you would have:

```

mysql -u *UserName* -p *databaseName* < *sqlFile.sql* > queryResults.txt

```

---

### Post by benevolent on 2007-08-23
hmm, thx!!!! and the file where it should be?? /usr/share/mysql ???


I ' m having at my desktop the sql file, so i open the terminal and do that:

```
dimitris@dimitris:~/Desktop/&#902;&#963;&#954;&#951;&#963;&#951;3$ mysql -u root -p dbname < dblab_tm6_2007.sql 
Enter password: 
ERROR 1049 (42000): Unknown database 'dbname'
```

:(

---

