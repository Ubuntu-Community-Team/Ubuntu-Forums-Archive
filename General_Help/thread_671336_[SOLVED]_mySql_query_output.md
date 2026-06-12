---
title: "[SOLVED] mySql query output"
date: 2008-01-18
forum: General Help
---

### Post by Keith Hedger on 2008-01-18
Hi simple question but i can't seem to find the answer!
when i query a database using (for instance)```
 mysql  -u root -p"?????" -e"use codes;" -e"select website from passcodes where name=\"yahoo\";"
```
i get :```
+-----------------+
| website         |
+-----------------+
| www.yahoo.co.uk | 
+-----------------+
```

but i just want the data without all the table stuff, i know i can use string slicing to pretty it up but there must be a way of getting the data on its own.
Thanks in advance:)

---

### Post by Keith Hedger on 2008-01-18
found the answer not immediatly obvious!
```
 mysql  --silent --skip-column-names
```

---

