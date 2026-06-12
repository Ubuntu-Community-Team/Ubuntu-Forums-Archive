---
title: "Nothing can connect to mySQL"
date: 2018-09-25
forum: General Help
---

### Post by Adam_GUI on 2018-09-25
I wanted to try and get LemonPOS set up.

I'm following instructions from [this post]("https://ubuntuforums.org/showthread.php?t=1526096&p=11373244#post11373244") which reads as follows:
> 
 October 20th, 2011 #6
Motovista
First Cup of Ubuntu 

Here is how I did it in Kubuntu:

Terminal command- sudo apt-get install mysql-client mysql-server

download Lemon POS from Software Repository

Terminal command- cd /usr/share/kde4/apps/lemon/

Terminal command- cat lemon_mysql.sql | mysql -u root -p

Reboot and open Squeeze. There will be a username and password on the screen that logs into the database. Leave that alone. I think this is where most people (I did) have issues with the program, because they think they are supposed to put their mysql password or the default lemonpos username and password there.

Where you are asked for a user name and password, use admin and linux. 

I installed LemonPOS and Squeeze from the 18.04 repos.
I understand that the software is old and unmaintained, as the wiki links for it are gone and the domain for sale.

Anyway.

My underlying problem is with mySQL.
I don't remember being prompted for a password at install.

I have run the following to change my root mySQL password:
```
sudo mysql_secure_installation
```

I've run CD to get to /usr/share/kde4/apps/lemon

When I run:
```
cat lemon_mysql.sql | mysql -u root -pls
```
I get the return of:
```
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 1698 (28000): Access denied for user 'root'@'localhost'
```

When running the same as sudo:
```
sudo cat lemon_mysql.sql | mysql -u root -pls

```
I get the return:
```
mysql: [Warning] Using a password on the command line interface can be insecure.
ERROR 1698 (28000): Access denied for user 'root'@'localhost'
```
Then, a Sudo password prompt, and a return of new line.

Running LemonPOS at this stage gives me a warning that it could not connect to database, and the logout function fails.  So, I have to kill it with CTRL+ALT+ESCAPE.

I know what my mySQL root password is.  But, I'm never prompted for it.

I know I'm missing something.  I just don't know what.

Any clues?

---

### Post by Adam_GUI on 2018-09-27
Bump?

So, I've also tried unicenta POS 4.4.2.
There are multiple problems with the setup.

I'm following the guide posted here:
[https://chubbable.com/unicenta-3-9-ubuntu-16-install-guide#step-3-download-and-install-unicenta-pos]("https://chubbable.com/unicenta-3-9-ubuntu-16-install-guide#step-3-download-and-install-unicenta-pos")

The initial install goes fine.
CD -ing to /opt/unicentaopos-4.4.2 and making the SH files boot-able works.

Running
sudo sh start.sh returns:
> : not found0: start.sh: 
: not found3: start.sh: 
: not found6: start.sh: 
start.sh: 28: start.sh: Syntax error: word unexpected (expecting "in")


Running sudo sh configure.sh returns:
> : not foundh: 20: configure.sh: 
: not foundh: 24: configure.sh: 
Error: Could not find or load main class com.openbravo.pos.config.JFrmConfig


However, running java -jar unicentaopos.jar launches the program.
It returns this in terminal:
```
Sep 27, 2018 7:48:13 PM com.openbravo.pos.forms.StartPOS$1 run
WARNING: Look and Feel is set
Thu Sep 27 19:48:15 EDT 2018 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
Thu Sep 27 19:48:15 EDT 2018 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.

```

The program's GUI issues this:
```
Database manager message
DNG_00_0000
Danger: Unable to connect to database: Database not available.
```

So, my underlying issue looks to be mySQL?
I added a unicentaopos database to mySQL.  But, not matter what settings I give, I can't connect to it.

---

### Post by Adam_GUI on 2018-10-06
Bump.
I've uninstalled and reinstalled mysql server and client with no change with Lemon/Squeeze, unicentaopos, or TOra.
I can access mysql, but, only through sudo at command line.

I tried again to cat the lemon SQL file into the main database and get access denied at command line, even with the correct password.

I'm open to ideas.

---

### Post by Adam_GUI on 2018-10-09
I had tried to setup a point of sale system.
I only want things to connect at localhost.

I'm sorry if this seems like duplication of asking for help.  
But, my target shifted on me and I think this thread is more direct to my underlying problem.

I can only log into mySQL with sudo.  
```
select host, user from mysql.user;

```
lists my users as:
```

+-----------+------------------+
| host      | user             |
+-----------+------------------+
| localhost | debian-sys-maint |
| localhost | mysql.session    |
| localhost | mysql.sys        |
| localhost | root             |
+-----------+------------------+

```

I've been trying to setup LemonPOS and Unicentaopos.
Only nothing can connect to the local database.

I clearly have no clue as to what I'm doing on the mySQL side.

I have TOra installed as a GUI interface for mySQL and it can't connect either.

I have no clue what I've done wrong.

I guess what I'm asking for is suggested reading for setting up mySQL.
The man page is a little too technical for me at this point.

I'll even take a book recommendation.

Thanks.

---

### Post by DuckHook on 2018-10-09
Please do not duplicate post as this confuses those trying to help and dilutes community effort.

It is perfectly acceptable to bump your thread every 12 hrs to float it up from the bottom of the sea.

---

### Post by Adam_GUI on 2018-10-09
> **DuckHook said:**
> Please do not duplicate post as this confuses those trying to help and dilutes community effort.

It is perfectly acceptable to bump your thread every 12 hrs to float it up from the bottom of the sea.

This is fair.
Sorry about my confusion.

---

### Post by SeijiSensei on 2018-10-10
```
Thu Sep 27 19:48:15 EDT 2018 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
```

Did you read the error about SSL?  You either need to configure certificates and the like, or not use SSL.  If you're only connecting to the server itself via the localhost interface, SSL isn't necessary.  Take a look at 

[https://stackoverflow.com/questions/34189756/warning-about-ssl-connection-when-connecting-to-mysql-database](https://stackoverflow.com/questions/34189756/warning-about-ssl-connection-when-connecting-to-mysql-database)

---

### Post by Adam_GUI on 2018-10-10
> **SeijiSensei said:**
> ```
Thu Sep 27 19:48:15 EDT 2018 WARN: Establishing SSL connection without server's identity verification is not recommended. According to MySQL 5.5.45+, 5.6.26+ and 5.7.6+ requirements SSL connection must be established by default if explicit option isn't set. For compliance with existing applications not using SSL the verifyServerCertificate property is set to 'false'. You need either to explicitly disable SSL by setting useSSL=false, or set useSSL=true and provide truststore for server certificate verification.
```

Did you read the error about SSL?  You either need to configure certificates and the like, or not use SSL.  If you're only connecting to the server itself via the localhost interface, SSL isn't necessary.  Take a look at 

[https://stackoverflow.com/questions/34189756/warning-about-ssl-connection-when-connecting-to-mysql-database](https://stackoverflow.com/questions/34189756/warning-about-ssl-connection-when-connecting-to-mysql-database)

I've read the article.  
Here's what I've done so far.

I converted configure.sh and start.sh with dos2unix.  So, they run now.
I do not get an SSL warning when launching "./configure"

I granted all privileges to my local user in mySQL with:
```
grant all privileges on * . * to 'MYUSER'@'localhost';
```

Here's what my database setup tab looks like:
[ATTACH=CONFIG]281288[/ATTACH]
My user is different in execution.  But, I'm not posting the real user name in the screenshot.

I've appended the line DB1URL to read:
```
jdbc:mysql://localhost:3306/unicentaopos?zeroDateTimeBehavior=convertToNull&&useSSL=false
```

I have actually created a database called "unicentaopos".

I was able to connect on test!  Hooray!

I'm running "./start.sh".

Things were going okay until I got this dialogue box:
[ATTACH=CONFIG]281289[/ATTACH]

Terminal output at this point is as follows:
```
Oct 10, 2018 2:35:10 PM com.openbravo.data.loader.PreparedSentence openExec
INFO: Executing prepared SQL: INSERT INTO applications(id, name, version) VALUES(?, ?, ?)

```

However, running "./start.sh" again gives me the start page.  Looks like I'm in.
[ATTACH=CONFIG]281290[/ATTACH]

So, success?

I get to play around with a point of sale system now.  So, I'll mark the thread as solved.

---

### Post by 1aqeel on 2019-01-17
[COLOR=#242729][FONT=Arial]Answer from ->> [https://www.youtube.com/watch?v=qr-t8ksYO78](https://www.youtube.com/watch?v=qr-t8ksYO78)[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]go to my.cnf file, note that you will find multiple my.cnf file, i had to look at all of them to find this->[/FONT][/COLOR]
# The MySQL server
[mysqld]
user = mysql
port=3306
socket      = /opt/lampp/var/mysql/mysql.sock
[COLOR=#242729][FONT=Arial]Copy the path and write it like ->[/FONT][/COLOR]
mysql -u root -p --socket=/opt/lampp/var/mysql/mysql.sock 
[COLOR=#242729][FONT=Arial]Thanks[/FONT][/COLOR]

---

### Post by Adam_GUI on 2019-01-17
Actually marked the thread as solved, as I've had this running for about three months now with no issue.
The Google Translating of my post into something else and back into English is kind of amusing.  But, it's happened twice now.

I'm assuming it's a bot doing it.

I don't particularly want to ask for a thread lock in case someone else has a similar issue.

---

