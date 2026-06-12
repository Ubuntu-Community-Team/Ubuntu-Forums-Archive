---
title: "crontab -e problems, probably my syntax or understading?  16.04 server CLI."
date: 2018-12-31
forum: General Help
---

### Post by adrian-h on 2018-12-31
I am asking about crontab -e   to run a backup job every day to back up a mysql database file

If I run this in command line it works

```
adrian@localhost=$ mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/backup.sql;

```
The 2> /dev/null redirects a warning I get on the screen normally "mysqldump: [Warning] Using a password on the command line interface can be insecure." and I end up with the file backdb.sql in my home directory.

when I use this line in crontab -e

```

06 12 * * *  mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/traccarbackup.sql;

```

I do not get the output file.  I can see that the job runs in top briefly but when I check /var/log/syslog I see an error message as follows:

Jan  1 00:06:01 home-tracker CRON[6600]: (adrian) CMD (mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/backup.sql;
Jan  1 00:06:01 home-tracker CRON[6599]: (CRON) info (No MTA installed, discarding output)

I appreciate there is no mail server installed but wondering what I have got wrong?  Is it something basic like it will only run a script file in crontab -e.  

I wonder about this, because if I make a bash script:

Called daily

```

#!/bin/bash
# daily to backup database datadb

mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/backup.sql;
#

```

```
adrian@localhost=$ chmod +x daily
```

crontab -e now just contains

```

06 12 * * * /home/adrian/daily

```


It works as expected, so is it script only or have I something obvious wrong?

Cheers

Adrian

---

### Post by clementc on 2018-12-31
Hi Adrian,

Can you please modify your CRON (crontab -e) job to the following so that we can look at the output after it runs:

mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/backup.sql >> /home/adrian/outputlog 2>&1

Please run the job through CRON and report back the data contained in outputlog (located at /home/adrian/), please make sure to remove any sensitive information first.

---

### Post by Tadaen_Sylvermane on 2018-12-31
Path problem most likely. Environment variables aren't set in crontab by default. I get around this with a PATH line in my crontab as so. This is from my user on my server. Ubuntu 16.04. To get the below output I just run ```
echo $PATH
``` Paste the result into the crontab like so.

```
PATH=[FONT=monospace][COLOR=#000000]/home/jason/bin:/home/jason/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin[/COLOR]:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin[/FONT]
```[FONT=monospace]

Yours would be different on the username only. I do this for each user including root at first installation. Solves many problems right off the bat. Other option is to use full path in your crontab. Like so.

[/FONT]```
[FONT=monospace][COLOR=#000000]/usr/bin/mysqldump[/COLOR][/FONT]
```[FONT=monospace][COLOR=#000000]

instead of

```
mysqldump
```
[/COLOR][/FONT][FONT=monospace]
[/FONT]

---

### Post by spjackson on 2019-01-01
> **adrian-h said:**
> 
```
adrian@localhost=$ mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/backup.sql;

```

I am very confused. As I understand it, mysqldump writes the backup to standard output and its syntax is:
```

mysqldump [options] [db_name [tbl_name ...]]

```
In none of the commands you have shown, i.e. none of the working ones and none of the not working ones, do you ever redirect standard output.

Again, as I understand it, the **parameter** /home/adrian/backup.sql should interpreted as a tablename and therefore fail.

So, I'd expect your crontab entry not to work because you are not redirecting standard output and providing a file path as a tablename parameter. However, I would expect all your working examples not to work either for the same reasons.

Finally, I don't know what that semi-colon is doing there: it separates shell commands but there is no 2nd command. It is superfluous.

Yes, I'm definitely confused... unless you have a customised mysqldump (e.g. in ~/bin) that's a wrapper for the standard one and treats parameters differently. In that case, the customised wrapper could be doing redirection and when run from cron the customised version wouldn't be in the path. No, that can't be it because your /home/adrian/daily would then not work from cron.

---

### Post by adrian-h on 2019-01-01
@clementc

OK I changed the crontab -e line to:

```
20 9 * * * mysqldump -u datauser -pdatapass --opt datadb 2> /dev/null /home/adrian/backup.sql >> /home/adrian/outputlog 2>&1
```

and let it run, again no backup.sql file but here is the content of outputlog, it makes no sense to me, but that will be because I do not understand it yet!

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
 SET NAMES utf8mb4 ;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;



@Taedan_Sylvermane

You are on to something!

As I use a remote ssh shell to get into the unit, (it sits in the corner with no keyboard or screen!) I used echo $PATH > /home/adrian/echolog

The output of echolog was just:

/usr/bin:/bin

Where as command line output of echo $PATH is:

/home/adrian/bin:/home/adrian/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin

So I modified the crontab -e line with /usr/bin to be:

```

10 10 * * * /usr/bin/mysqldump -u traccaruser -ptraccarpass --opt traccardb 2> /dev/null /home/adrian/backup.sql >> /home/adrian/outputlog 2>&1

```

Still no backup.sql generated and the new outputlog was:

mysqldump: [Warning] Using a password on the command line interface can be insecure.
mysqldump: Couldn't find table: "/home/adrian/backup.sql"
-- MySQL dump 10.13  Distrib 8.0.13, for Linux (i686)
--
-- Host: localhost    Database: datadb
-- ------------------------------------------------------
-- Server version       8.0.13

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
 SET NAMES utf8mb4 ;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;


So looks like the issue goes a bit deeper.

The change to /usr/bin/mysqldump got the program to run at least.  But it looks as though it will not generate the backup.sql file

I changed the line to be 

```

10 10 * * * /usr/bin/mysqldump -u traccaruser -ptraccarpass  --opt traccardb /home/adrian/backup.sql >>  /home/adrian/outputlog 2>&1

```

Again no backup.sql and the outputlog contents is the same as previous with mysqldump: Couldn't find table: "/home/adrian/backup.sql"

@spjackson

You must forgive me in that redirection in fact all of this is at a level I am only just trying to achieve,  Learning this should have been something I did in my early years not at this stage but it keeps the brain cels running.

The redirect was initially done in command line so that I did not get the password warning message on the screen but it still generated the outut.

From crontab -e running the script backup.sql is all there and correct as the first few lines show:

-- MySQL dump 10.13  Distrib 8.0.13, for Linux (i686)
--
-- Host: localhost    Database: traccardb
-- ------------------------------------------------------
-- Server version    8.0.13

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
 SET NAMES utf8mb4 ;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `DATABASECHANGELOG`
--

DROP TABLE IF EXISTS `DATABASECHANGELOG`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
 SET character_set_client = utf8mb4 ;
CREATE TABLE `DATABASECHANGELOG` (
  `ID` varchar(255) NOT NULL,
  `AUTHOR` varchar(255) NOT NULL,
  `FILENAME` varchar(255) NOT NULL,

etc

Thank you all for your time, I am confused and needing breakfast, back soon.

Adrian

p.s.

the ; was left over from me typing within mysql  it seemed to need the ; as a end of line otherwise it sat there waiting for one?  It is probably not needed and has not been included on several attempts.

---

### Post by The Cog on 2019-01-01
it looks like this command is asking it to dump table /home/adrian/backup.sql and write it to /home/adrian/backup.sql:
```
10 10 * * * /usr/bin/mysqldump -u traccaruser -ptraccarpass  --opt traccardb /home/adrian/backup.sql >>  /home/adrian/outputlog 2>&1
```
I suspect that is a copy/paste error and you should remove the table name so it looks like this:
```
10 10 * * * /usr/bin/mysqldump -u traccaruser -ptraccarpass  --opt traccardb > /home/adrian/outputlog 2>&1
```

P.S.
I would use > instead of >>, so as to overwrite the backup file rather than appending it with another copy. Have edited my suggested line accordingly.

---

### Post by adrian-h on 2019-01-01
@The cog

Sorry I did make some editing errors there, I am dealing with a database file called traccerdb etc but tried to make the lines more generic so was calling it datadb etc but I forgot!


The >> adition was just something I was asked to include in a post from clementc to provide some more error output into a file named output log, the backup.sql was meant to be the output from mysqldump and it  worked as a script.

So I have done a crontab -e more in line with the original idea without the warning message redirect, I did the 2> /dev/null as I originally thought it was the password warning message was stopping mysqldump.

```

00 12 * * * /usr/bin/mysqldump -u datauser -pdatapass --opt datadb > /home/adrian/backup.sql

```

***That now worked part of the output file backup.sql is as follows***:

-- MySQL dump 10.13  Distrib 8.0.13, for Linux (i686)
--
-- Host: localhost    Database: traccardb
-- ------------------------------------------------------
-- Server version       8.0.13

/*!40101 SET @OLD_CHARACTER_SET_CLIENT=@@CHARACTER_SET_CLIENT */;
/*!40101 SET @OLD_CHARACTER_SET_RESULTS=@@CHARACTER_SET_RESULTS */;
/*!40101 SET @OLD_COLLATION_CONNECTION=@@COLLATION_CONNECTION */;
 SET NAMES utf8mb4 ;
/*!40103 SET @OLD_TIME_ZONE=@@TIME_ZONE */;
/*!40103 SET TIME_ZONE='+00:00' */;
/*!40014 SET @OLD_UNIQUE_CHECKS=@@UNIQUE_CHECKS, UNIQUE_CHECKS=0 */;
/*!40014 SET @OLD_FOREIGN_KEY_CHECKS=@@FOREIGN_KEY_CHECKS, FOREIGN_KEY_CHECKS=0 */;
/*!40101 SET @OLD_SQL_MODE=@@SQL_MODE, SQL_MODE='NO_AUTO_VALUE_ON_ZERO' */;
/*!40111 SET @OLD_SQL_NOTES=@@SQL_NOTES, SQL_NOTES=0 */;

--
-- Table structure for table `DATABASECHANGELOG`
--

DROP TABLE IF EXISTS `DATABASECHANGELOG`;
/*!40101 SET @saved_cs_client     = @@character_set_client */;
 SET character_set_client = utf8mb4 ;
CREATE TABLE `DATABASECHANGELOG` (
  `ID` varchar(255) NOT NULL,
  `AUTHOR` varchar(255) NOT NULL,
  `FILENAME` varchar(255) NOT NULL,
  `DATEEXECUTED` datetime NOT NULL,

etc

So it looks as though my errors where two fold, 

1)  one I had to include the /usr/bin/mysqldump as said by Tadaen_Sylvermane 

2) my original 2> /dev/null redirect of the warning message was also causing an issue, when really I did not need to include it!

I am thinking that spjackson was referring to that in his post but it was beyond my comprehension at that point, sorry.

I will have to study a book on mysql and one on Linux admin when they arrive and try and figure why there is a difference between command line, scripted lines and mysqldump when it comes to redirecting STDERROR.

But for now I have a working idea of things, I will tidy things up at this end and have two lines in crontab -e .  One to run as script and one not, just to prove to myself I can get them to work and report back later.

Again big thanks to all for assistance.

Adrian

---

### Post by adrian-h on 2019-01-01
I tried adding the Path to crontab -e

as in:

crontab -e
 ```
# set PATH same as user!
PATH=/home/adrian/bin:/home/adrian/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
#
# m h  dom mon dow   command
# This is to backup datadb as a sql.gz file daily
10 15 * * * /home/adrian/daily
14 15 * * * mysqldump -u datauser -pdatapass --opt datadb | gzip > /home/adrian/datadb_1514_`date '+%d-%m-%Y'`.sql.gz
```

The script at 15:10 still works but the command line in crontab -e  at 15:14 does not, I assume that I still have something not correct, or I have not grasped the concept yet.

I will have to give up for a while as I have to have family time.

I wish you all a "Happy new year".


I will come back when I can probably tomorrow!

Adrian

---

### Post by clementc on 2019-01-01
Hi Adrian,

Can you please try escaping % character with \ like this for your crontab -e command:

mysqldump -u datauser -pdatapass --opt datadb | gzip > /home/adrian/datadb_1514_`date +\%d-\%m-\%Y`.sql.gz

Happy New Year to you too!

---

### Post by adrian-h on 2019-01-01
@clementc=d>=d>=d>

Thank you , thank you and thank you again.


It works, now I thought the escape characters were only for printing.  But it gives me another bit to the general puzzle that is linux administration.

I have made a ~/scripts/ and ~/backups/ backups folders to both store any scripts into and save the backups to to keep the home directory a bit more organised.

What is a real pain in the butt is that the original idea was from a website about automatically backing up under linux.

[https://www.backuphowto.info/how-backup-mysql-database-automatically-linux-users](https://www.backuphowto.info/how-backup-mysql-database-automatically-linux-users)

I can now understand why many just stick to using scripts as it fewer pitfalls, but for me learning it is good to find them in these early stages.

I still get the message in syslog Jan  1 22:10:04 home-tracker CRON[3903]: (CRON) info (No MTA installed, discarding output)
Which I still assume is down to the password warning about using -pdatapass, but I will live with that for a while and play some time later for this knowing I have a working crontab.

Again thanks for everyone's assistance.  Hope this post can help some others sometime.

Adruian

---

### Post by clementc on 2019-01-01
Hi Adrian,

I am glad to hear that your problem is now resolved.

Regarding the (CRON) info (No MTA installed, discarding output) message that you are still getting, this is due to the fact that your cron task produces an output that the cron daemon then tries to email you.

To solve this, the easiest option (if you do not need the output to be emailed to you) is to add MAILTO="" to your crontab (do not put anything else on this line, not event #comments, or this won't work).

Another option would be [FONT=arial]to add[/FONT] >/dev/null 2>&1 [FONT=arial]at the end of your command to discard the produced output.[/FONT]

If you do need the output produced by your command to be emailed to you, you should install [postfix]("http://www.postfix.org/"). Please advise if you require assistance configuring it to work with cron.

---

### Post by adrian-h on 2019-01-01
Thanks I will add MAILTO="" under my PATH= line and the hope it does not raise it's head again.

I will probably play at some point in the future, I can only seem to learn by doing, changing things and seeing what happens.  I do find it confusing that there are so many interpretations to do a task and seem to depend on the version one is using.

A bit of why I am doing this.

basically to keep my maind active and to force myself to learn, think logically and hope to not get that far behind the younger generation.

I am using a couple of very cheap HP thin clients a T5730 and T5740 cost less than £20 each, around I guess $25 each, being 32 bit PC's I am stuck on 32 bit 16.04.  The T5740 is max of 12 Watts and the T5730 24 watts consumption so very small costs, they are both fan-less and small.

One is running a vehicle tracking server for home use, so I will not cause any problems if I mess them about to much, the idea is to learn in stages, installation, running, apache2, back-up and recovery and general linux operation.  Doing it all command line rather than graphically means I have to learn commands.

So watch out I could well be back when it comes to restoring data, but I will have a good go first.

Again thanks.

Adrian

Just tried the MAILTO="" line and the messages no longer show in syslog so that completes that task, time for sleep at this end.

---

### Post by clementc on 2019-01-01
Hi Adrian,

It is great to meet learning people of all ages. I myself just started in the Linux world (have been using Windows for more than 25 years now) and decided to try helping as much as I can as I believe that it is the best way to learn and share in the spirit of open source.

Good luck in your learning endeavors.

See you around.

Clement

---

