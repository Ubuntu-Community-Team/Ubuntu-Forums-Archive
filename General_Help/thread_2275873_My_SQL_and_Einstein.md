---
title: "My SQL and Einstein"
date: 2015-04-29
forum: General Help
---

### Post by janeku2 on 2015-04-29
Hi to every one.
I tried to install one software that depends of My SQL and Pythi, called Einstein.
I am not experienced user so reading some articles I made to create needed database and give privileges to root user under my SQL.
In INI file of Einstein there is:
[GUI]
TEST:TEST
LANGUAGE:en
[DB]
ENCODING:
DBHost:localhost
DBPass:root
**MYSQLBIN:C:\Program Files\MySQL\MySQL Server 5.1\bin**
DBName:einstein
DBUser:root


Looks like there are lefts from Windows installation procedure so I think I have to change bolded line with proper one under Ubuntu. Unfortunately I do not know where MySQL bin is located in my computer folders. I use 64 bit Ubuntu 14.04.2 LTS and installed Python and MySQL from software center.
Also, here is link [http://einstein.sourceforge.net/users/installation.html#einsteindb-manual](http://einstein.sourceforge.net/users/installation.html#einsteindb-manual)to manual so any help regarding proper installing of this software is welcome.
Regards,

---

### Post by yancek on 2015-04-29
You can find the location of most mysql files by opening a terminal and typing:  whereis mysql
Not sure which one you need or if it will work.  Did you use the very general instructions at the bottom of the page for Linux at the linked site?

---

### Post by janeku2 on 2015-04-29
Hi,
I think I managed to solve this with a little help of author of Einstein.

I'll try to post a little guide for it:

1. Download Einstein ZIP on link above.

2. Extract to some folder

3. Download Python , MySql and other dependencies explained and suggested in link

[LIST]
[*]Python (Version 2.6 or higher but not 3.x) 
[*]MySQL (Version 5.1 or higher) 
[*]several Python complements:
[LIST]
[*]wxPython 
[*]matplotlib 
[*]numpy 
[*]MySQL-Python 
[/LIST]
  
[/LIST]

4. Make in MySql databese named "einstein" (without quotes)
    mysql -u root -p
    create database einstein;
    show databases

5. Create user root with password root in MySQL
    CREATE USER 'root'@'localhost' IDENTIFIED BY 'root';

6. Grant privileges to einstein database
    GRANT ALL PRIVILEGES ON einstein.* TO 'root'@'localhost';

7. Refresh
    FLUSH PRIVILEGES;

8. Go to the directory of your EINSTEIN installation, subfolder sql

cd YOURPATH/einstein/sql

9. Then open your database with the command:

mysql -h localhost -u root -p root

10. Once you are within the menu of MySQL you can check database status this with the command:

     show databases;

     You should get a list of some database names, including "einstein".

11. Activate the EINSTEIN database with the command:

      use einstein;

12. In order to check if you did well, you can check which tables are 
already in your database, using:

       show tables;

If there are no tables in your database, there probably has been some 
error during setup.

13. Load the einstein default database from the file einstein.sql

      source einstein.sql;

14. Check the result:

Typing again "show tables;" now you should see a long list of tables 
forming the einstein database.

15. Run EINSTEIN with command :

     python einsteinMain.py 

     stationed in folder YOURPATH/einstein/src/GUI

I think this is it.

Now the main problem for me is how to make executable script that will be started , go to '~/einstein/src/GUI' and run command 'python einsteinMain.py' .For this any help is welcome.

---

