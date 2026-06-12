---
title: "workbench doesn't start"
date: 2015-01-21
forum: General Help
---

### Post by johnnybgoode on 2015-01-21
what's wrong with this syntax?

mysql> mysql-workbench;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'mysql-workbench' at line 1

---

### Post by Holger_Gehrke on 2015-01-21
Are you trying to start mysql-workbench inside the mysql command line client ? 

That won't work, because the mysql command line client expects you to enter SQL queries for the server to execute. To start mysql-workbench, use the Dash in Unity, the menu in other desktop environments or mysql-workbench in the shell. And if your  machine isn't fast and doesn't have a generous amount of RAM, be prepared to wait not just for the startup but for everything. .

---

### Post by johnnybgoode on 2015-01-21
[SOLVED]

It will not start from within msql. I opened a new terminal en typed "msql-workbench"

---

