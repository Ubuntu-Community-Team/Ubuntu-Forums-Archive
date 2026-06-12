---
title: "Create Table[IF NOT EXIST]"
date: 2008-06-04
forum: General Help
---

### Post by Black Mage on 2008-06-04
I am creating a datbase interface using Java and there is this error when I try this SQL Statement:

CREATE TABLE [IF NOT EXISTS] 06_2008_Running_Log 

it throws this error:

com.mysql.jdbc.exceptions.MySQLSyntaxErrorException: You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '[IF NOT EXISTS] 06_2008_Running_Log


And I it works when I take the [IF NOT EXISTS] out. Any ideas why this is happening when this is proper sql syntax?

---

