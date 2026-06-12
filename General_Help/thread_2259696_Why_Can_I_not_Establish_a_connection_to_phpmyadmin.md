---
title: "Why Can I not Establish a connection to phpmyadmin"
date: 2015-01-06
forum: General Help
---

### Post by alan41 on 2015-01-06
Hi 
I have successfully installed a WAMP server on a laptop which allows me to create a database.

I wanted to then use the same software on another LINUX XUBUNTU machine so I attempted to install LAMP but I followed several tutorials of the internet and always got the same result when entering localhost in my browser:

**Firefox can't establish a connection to the server at localhost.**

I think all the necessary software is installed i.e. apahce2   phpmyadmin    php5    mysql-server  

1. So am I being thick is it not possible to have two PC's on the same network accessing localhost ?
2. Does localhost apply to the pc or to the LAN ?
3. Is there a better way by me accessing the database on the WAMP laptop from my UBUNTU PC ?

any help appreciated I am a novice blundering around in the dark.

---

### Post by Holger_Gehrke on 2015-01-06
localhost is a symbolic name for the machine on which you are working. When you are accessing localhost through the network, the computer is talking to itself. If you want to access the database on the other machine, you need the other machine's name or network address. Depending on how well you know SQL there's way more options for accessing the database than through phpmyadmin.

There's of course the question of whether or not the database is set to answer requests from the network or will only listen on the loop back interface (it's usually configured that way for security reasons).

---

### Post by alan41 on 2015-01-06
Many thanks for that clarification.
Put simply I would like to have my database on a different (Desktop Xubuntu) PC to the one it is currently on i.e. a laptop (WIN7)
I can export my database file in SQL so what is the simplest way to put the database on the (Desktop Xubuntu) PC as my attempts to install and access phpmyadmin on it have so far failed.
I am a complete beginner at SQL.....but have a book for reference.

---

### Post by Holger_Gehrke on 2015-01-06
So you have a dump of the database and want to import it into MySQL on your Desktop machine.
Enter this
```

mysql -u 'username' -p'passwort' 'databasename' < 'backupfile'

```
in the terminal, replacing 'username', 'passwort', 'databasename' and 'backupfile' as needed. (the missing space between -p and 'password' is **not** a typo; there must not be a space there).
After this has finished, you can use the same command without the "< 'backupfile'" to enter a interactive SQL-shell and run a few select-queries to see that everything has transferred.

---

### Post by alan41 on 2015-01-06
OK Thanks, I will give it a try in the morning......I still have a lot to learn !

---

### Post by alan41 on 2015-01-20
Hi There
I have managed to install the Apache2 web server on my Xubuntu machine which starts with Apache2 Ubuntu Default Page.

This page tells me to replace the index file located at /var/www/html/index.html  But it does not say what with !!

I want to run phpmyadmin (which is installed) when I enter the command localhost/phpmyadmin as I do on my other windows7 machine.

So how do I do this?

---

### Post by Holger_Gehrke on 2015-01-20
If you installed phpmyadmin through the package manager, it should have asked during installation what webserver to configure for use with phpmyadmin, the administrator password for the database and a password for access to phpmyadmin. It should then have created an additional configuration file for apache in '/etc/phpmyadmin/apache.conf' and changed the main apache configuration to load this. This configuration contains an alias, which makes the directory where mysqladmin is installed ('/usr/share/phpmyadmin') appear as 'http://localhost/phpmyadmin'. So if you've gone through the package manager for installation, you're done already and it should just work.

If you've done it some other way, well, "I pity the fool who does it some other way !" as Mr. T would say ...

---

### Post by alan41 on 2015-01-21
I installed phpmyadmin using sudo apt-get install phpmyadmin 

I am not sure if this is "through the packet manager" or do you mean using the Software Centre ?

How do I completely uninstall phpmyadmin and start over ?

---

### Post by Holger_Gehrke on 2015-01-21
By "the package manager" I mean all the official tools that install software from the ubuntu repositories and/or PPAs. This includes the apt-* command line tools, aptitude, synaptic and the software centre. It doesn't include using 'dpkg -i' with a downloaded package file, unpacking an archive full of binaries or scripts in some directory on the $PATH or compiling something from source and installing it somewhere.

When I last installed phpmyadmin, I did so using synaptic, and it worked on the first try. I just now removed it and tried it through apt-get and ... it didn't ! The reason : when it asks for which webserver to configure for it, I just moved the cursor to apache and hit enter. **This is wrong** ! You have to move the cursor to the server you want **and hit the space bar** to make a selection **before** you hit enter. To fix this, it's not necessary to remove and reinstall. There's a tools to repeat the configuration process for installed packages. Its called 'dpkg-reconfigure'. So just call 'sudo dpkg-reconfigure phpmyadmin'. It will go through the same dialog with a few additional questions -- like the mysql user name for the mysql administrative user and the mysql user name for phpmyadmin -- and then configure the package right -- hopefully.

---

### Post by alan41 on 2015-01-23
That worked fine, many thanks for that I hit the space bar and I saw the asterisk appear to confirm selection, I would never have found that myself !!

I am now getting this error message (below)  and have input my password but not sure what my username is as I don't recall being asked for one.  
Is it the name that appears on the terminal ? 

This is what I am getting "#1045 Cannot log in to the MySQL server"

Thanks again, you are a treasure

---

### Post by Holger_Gehrke on 2015-01-23
MySQL keeps it's own user accounts. The MySQL administrator is named 'root' just like the Linux system admin (but it is a separate MySQL-internal account). The password is the one you chose during installation of MySQL.

---

### Post by alan41 on 2015-01-23
Hi Holger

root and my password worked and I now have exactly what I wanted thanks to your very much appreciated support.

If you ever need a painting visit my web site [www.alanswatercolours.co.uk](www.alanswatercolours.co.uk) 

alan

---

### Post by alan41 on 2015-01-24
Doh!

I am stuck again.

I thought the import / export commands would allow me to move my database from my Windows Machine to my Ubuntu machine but apparently not so.

So how do I create a 'dump' of my database?  I have read that the following command should do this but not sure where I would enter this command having tried cmd window and the SQL window within phpmyadmin without success.

shell> [B]mysqldump [*options*] --databases *db_name* ...

[/B]

---

### Post by Holger_Gehrke on 2015-01-24
It's been a few years since I used MySQL on windows, but it is **definitively** a command for the cmd window. But you have to either 'cd' to the directory where the mysqldump.exe resides or give the path to it on the command line.

What kind of trouble do the export and import functions of phpmyadmin make ?

---

### Post by alan41 on 2015-01-24
I exported an SQL file from my Windows machine using phpMyadmin but when I select the exported file for import into the Ubuntu machine (again using phpmyadmin) it generates a lot of syntax errors.

Am I correct in assuming it should transfer the database using this method ?  If so perhaps there is a version conflict !!

---

### Post by Holger_Gehrke on 2015-01-24
The exported file **should** be a simple text file with a few create (database, tables in the database) and a lot of insert statements. It might be compressed using gzip or bzip, then it would show an extension of .gz or .bz when downloading. Try to do the export again, but check the settings, especially the format, which should be set to "SQL" because that's what the import expects to get.

---

### Post by alan41 on 2015-01-25
OK Thanks I have now transfered a table what I was doing to get this error   

#1046 - No database selected 

I was not selecting a database to import to Doh!   Still I am getting better !!

---

