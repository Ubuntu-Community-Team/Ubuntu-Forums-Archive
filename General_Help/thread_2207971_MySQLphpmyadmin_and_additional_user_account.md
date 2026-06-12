---
title: "MySQL/phpmyadmin and additional user account"
date: 2014-02-26
forum: General Help
---

### Post by alain.roger on 2014-02-26
[COLOR=#000000][FONT=verdana]Hi, [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]i installed Ubuntu 13.10 to create a web development platform. [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]in MySQL(Server version: 5.5.35) i created a user with the following statement (in phpmyadmin): [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]CREATE USER 'myuser'@'*' IDENTIFIED BY 'mypass'; [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]GRANT ALL PRIVILEGES ON *.* TO 'myuser'@'*' WITH GRANT OPTION; [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]FLUSH PRIVILEGES; [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]1. in command line tool, i can connect with this user using NO password :( but i can't perform any action. [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]2. in phpmadmin, i can NOT connect to mysql and get the following error message: [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]#1045 Cannot log in to the MySQL server [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]so where is the problem ? [/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]thx a lot.[/FONT][/COLOR]

---

### Post by alain.roger on 2014-02-26
additional information:
I want this use (myuser) to connect from any host that's why i have the start "*" as host.
i know that in command line/MySQL statement, it should be replaced by a percentage "%"... but in both case it doesn't work.

---

### Post by alain.roger on 2014-02-27
ok i finally found the issue. Under MySQL 5.5.35 wildcard * is notanymore accepted...only the %.

---

### Post by monkeybrain20122 on 2014-02-27
Mysql allows root to log in without password but phpmyadmin does not, so to log into phpmyadmin as root you have to set up a root password in mysql as well.

---

