---
title: "how do I change the properties of a column in mysql"
date: 2015-01-21
forum: General Help
---

### Post by johnnybgoode on 2015-01-21
I have a table named "boek" and I try to make the id column auto increment.
what is the exact syntax, please?

mysql> select * from boek;
+---------------------------------------+-----------------+-------+----+
| titel                                               | auteur             | aard   | id |
+---------------------------------------+-----------------+-------+----+
| Sony-San S&W                             | W.Vandersteen   | strip |  0 |
| De 7 schaken S&w                        | W.Vandersteen   | strip |  0 |
| Bibber contra Tutter PP & BB          | Pom                 | strip |  0 |
| Het straalgas mysterie PP & BB       | Pom                | strip |  0 |

---

### Post by Holger_Gehrke on 2015-01-21
See [http://dev.mysql.com/doc/refman/5.7/en/alter-table.html](http://dev.mysql.com/doc/refman/5.7/en/alter-table.html) and for the column definitions [http://dev.mysql.com/doc/refman/5.7/en/create-table.html](http://dev.mysql.com/doc/refman/5.7/en/create-table.html).

So it should be something like "alter table modify column boeken integer auto_increment", replace integer with the actual datatype of the column.

---

### Post by johnnybgoode on 2015-01-22
Sorry, it doesn't work. I entered

[SIZE=3][/SIZE][SIZE=3] mysql> alter table modify column id (smallint auto_increment,PRIMARY_KEY (id));[/SIZE]
and get the message:

[SIZE=4]ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'column id (smallint auto_increment,PRIMARY_KEY (id))' at line 1[/SIZE]

Am I overlooking something?

---

### Post by Holger_Gehrke on 2015-01-22
If you read through the manual page for alter table i linked to, you will find an example which fits with what you want to do about a third of the way down in the page.
It should be:
ALTER TABLE boek MODIFY COLUMN id SMALLINT AUTO_INCREMENT;
Indices and keys are not changed with MODIFY COLUMN. You could also use CHANGE COLUMN instead of MODIFY COLUMN, but the you have to give the name of the column twice (change is for renaming and changing attributes, so you'd be renaming the column to the same name it had before). Take care to give **all** the attributes you want the column to have, it will be set to have exactly the attributes you set. For example, if you originally defined the column with NOT NULL and executed the statement above, the NOT NULL would be **removed** from the column definition.

---

