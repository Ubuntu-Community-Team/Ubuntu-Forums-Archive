---
title: "How to take a backup in MariaDB on Ubuntu 20.04?"
date: 2023-09-26
forum: General Help
---

### Post by anthonyaudi911 on 2023-09-26
Hello everyone, 
I apologize if I'm in the wrong forum. I'm trying to take a backup of my SQL database which is on MariaDB but I'm at a loss. I've tried the commands I see on the internet but everytime I press enter I am presented with another line that looks like this

-->

These are the commands I run from a terminal

sudu su <-- To get SU

mysql -u root -p <-- I can only successfully run this command if I use sudo su (I am not logged on as root but as another administrator


mysqldump -u root -p <-- Logs into MariaDB

SHOW DATABASES; <-- Shows my databases

mysqldump -u root -p  myDBName > /home/myusername/DB_backup.sql

When I press enter on the last line it just skips to the next line with a 

--> 

As if it's waiting for some kind of input. Am I doing something wrong?

Thanks

---

### Post by Tadaen_Sylvermane on 2023-09-26
I can't see your exact problem. Code tags help. That being said this is the script I use to dump my docker mariadb daily. Hasn't let me down yet. I haven't tested the restore part of the script. I do know my sqldumps restore as I had to reload one awhile back, just manually did the one.

[URL="https://gitlab.com/jmgibson1981/homescripts/-/blob/master/miscscripts/sqldumprestore.sh?ref_type=heads"]https://gitlab.com/jmgibson1981/homescripts/-/blob/master/miscscripts/sqldumprestore.sh?ref_type=heads


[/URL]*EDIT* Correction.

```
mysqldump -u root -p  myDBName > /home/myusername/DB_backup.sql
```

This needs to be run from the terminal, not inside the sql shell.

---

### Post by anthonyaudi911 on 2023-09-26
Hello, I honestly have no idea what is different from what you wrote and what I have. I even put them side by side to compare and they are identical. 
Whatever it is it works now, my DB is backed up.
Thanks though!

---

### Post by TheFu on 2023-09-27
[https://ubuntuforums.org/showthread.php?t=2311501&p=13431149#post13431149](https://ubuntuforums.org/showthread.php?t=2311501&p=13431149#post13431149) has a MariaDB backup script.

---

### Post by Holger_Gehrke on 2023-09-27
To make the difference between what you're doing and what Tadaen_Silvermane describes clear: you're entering the 'mysqldump' command into the SQL shell (/usr/bin/mysql). 'mysqldump' isn't a command in the SQL shell, it's a separate program and should be entered on the normal command line. SQL queries end in a ';' - it's done that way so you can easily enter multi-line queries. The '->' you see is the secondary prompt telling you to continue entering your query. If you had typed a ';' at the '->' prompt you would have gotten an error message telling you that the mysql shell doesn't know what to do with your input.

Holger

---

