---
title: "mysqldump question: Can I add several databases together?"
date: 2024-03-25
forum: General Help
---

### Post by zoomiest2 on 2024-03-25
I looked at a number of mysqldump tutorials, and didn't get the clarity I was looking for...

I have several database archives (made by mysqldump) of the same database - same schema.

If I load (restore) several on top of each other - won't it wipe out the last restored data? 

How can I add them all together? What is the command?

Thank you in advance!

---

### Post by dragonfly41 on 2024-03-25
Search for *merge* mySQL databases.

---

### Post by zoomiest2 on 2024-03-25
Thank you.

---

### Post by zoomiest2 on 2024-03-26
So, I found the INSERT INTO and REPLACE INTO commands for MySQL.
I have imported all of my mysqlsdump backs into new databases, so I can conform to the tutorials that I am reading about. I soon plan to run something like:

[COLOR=#000000][FONT=Arial]REPLACE INTO database1.[/FONT][/COLOR][FONT=Arial][COLOR=#6aa84f]**table1**[/COLOR][/FONT][COLOR=#000000][FONT=Arial] SELECT * FROM database2[/FONT][/COLOR][COLOR=#000000][FONT=Arial].table1

I read that the criteria (field) that will be compared, is "the unique identifier" (the table key?), and if it's the same, it will overwrite instead of insert a new row. Great - except that,

I would prefer to SPECIFY which field (often date_modified) is used as the unique identifier (instead of the system picking the table's key field each time).

How can I pick the field used as criteria in the REPLACE INTO command?

Just ALTER TABLE and pick a new UNIQUE INDEX according to my liking, then let the system do its work?[/FONT][/COLOR]

---

### Post by dragonfly41 on 2024-03-26
I focus more on NoSQL databases and my current interest (as I write) is merging multiple unstructured data bases:
But found these links which might add to your learning:
[https://dev.mysql.com/doc/refman/8.0/en/replace.html](https://dev.mysql.com/doc/refman/8.0/en/replace.html)
[https://stackoverflow.com/questions/616639/migrate-and-merge-several-databases-into-one](https://stackoverflow.com/questions/616639/migrate-and-merge-several-databases-into-one)
[https://www.mssqltips.com/sqlservertip/1704/using-merge-in-sql-server-to-insert-update-and-delete-at-the-same-time/](https://www.mssqltips.com/sqlservertip/1704/using-merge-in-sql-server-to-insert-update-and-delete-at-the-same-time/)
[https://www.sqlshack.com/understanding-the-sql-merge-statement/](https://www.sqlshack.com/understanding-the-sql-merge-statement/)
[https://www.databasestar.com/sql-merge/](https://www.databasestar.com/sql-merge/)
Source: Phind.com
[Query] When merging two SQL databases how can REPLACE INTO specify a target field?
There are more links.

---

