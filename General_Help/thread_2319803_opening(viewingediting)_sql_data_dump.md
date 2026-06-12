---
title: "opening(/viewing/editing) sql data dump"
date: 2016-04-07
forum: General Help
---

### Post by bjngchn on 2016-04-07
I know nothing about databases.  I have about 10G of .sql file.  How can I open it?   When I try to open it with something, like pico, computer freezes after a short while, and nothing happens.   I can install a trustable program if necessary (like something in repository). If so I need the command to do this.   Why can't I just double-click and open it?    Thanks.

---

### Post by SeijiSensei on 2016-04-07
Is it really a text file?  Try running "head -n100 /path/to/file.sql" to print the first hundred lines.

If it is a text file, copy the output from the head command here inside [noparse]```

```[/noparse] tags.

---

### Post by sander14 on 2016-04-07
what you also can do is this go to a CLI screen by pressing ctrl+alt+F1 or ctrl+alt+F2 log in using your credentials and then type in the following ```
less /path/to/your/file.sql
```
since what you said that the file is aprox. 10 GB working in a terminal is more light weight so you can read out your file if you really have to. After you are done reading it out with less press q 

also if you OWN the file (if the file is owned under your credentials and not root) and you want to edit the file use this command: ```
nano /path/to/your/file.sql
```
if you do not own the file well...

[COLOR=#ff0000]WARNING[/COLOR]: the following might harm and foul up the file and make your SQL server stop working if the file is one of the core SQL database files or is used by an other (important) program/daemon/module they might stop working too!!!! So be warned! :P

use this to edit the file as root (again not reccomended if you do not know what you are doing!!) ```
sudo nano /path/to/your/file.sql
```

If you are part of the sudo group (the group that allows you to run commands as root) it will ask you for your password after that nano will open and you are able to edit your file

when you are done press ctrl+x and say yes save the file and then Nano should exit

To return to your desktop env. do the following type exit if you are still in your shell env. till it asks for a log in again then after that use ctrl+alt+F7 to return to your desktop env.

hope this helped a lil bit

Good luck,

Sander

---

### Post by SeijiSensei on 2016-04-07
He said he tried to view the file with "pico," a text-based editor which is the predecessor to nano.  (I don't where he got that from; maybe an Alpine installation?)  My guess is that a 10 GB file is causing memory problems, which is why I suggested he start by using head to see just the top of the file.

---

### Post by sander14 on 2016-04-07
ah i see :) sorry my bad

---

### Post by bjngchn on 2016-04-07
Thanks for infos. head command works well (I can't post contents), but after 10000 lines it may take time to load or may freeze the computer (not a server). What I want is to have some control over this data. For example it would be great if I can search this data. Otherwise I may want to be able to make it smaller and smaller until it becomes easier for me to view "essential" data. Or to avoid memory problems I may want to split it  into 100 smaller files.  Command line search function would also be great. For example I type some keywords and only lines containing those keywords would be displayed. Nano doesn't work, I don't know why, but it might be related to size of the file (I'm shown a blank file). WHEN I do right-click in "open with" menu I'm shown Kate, Libre-Office, Okular. None of them seem to work, and some of them might freeze the computer.............It is a file containing several fields, it might be slghtly better if I can search by a specific field, or view the data in an alphabetical order corresponding to a field.

---

### Post by SeijiSensei on 2016-04-07
If it is a dump of an SQL database, you cannot simply slice it up into smaller files.  That's why I asked you to copy the top of the file and paste it here.  We really cannot help you otherwise, since I have no idea whether it comes from PostgreSQL, MySQL, or any of a number of other SQL databases.  Can't you open a terminal alongside your browser, run the head command, then highlight the text in the terminal and use copy/paste to put it inside of code tags here?  

We'd need to see things like CREATE TABLE definitions and the like.  For instance, here's the top of a PostgreSQL dump from a database on my server:
```

--
-- PostgreSQL database dump
--

SET statement_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = off;
SET check_function_bodies = false;
SET client_min_messages = warning;
SET escape_string_warning = off;

SET search_path = public, pg_catalog;

SET default_tablespace = '';

SET default_with_oids = false;

--
-- Name: brackets; Type: TABLE; Schema: public; Owner: mm; Tablespace: 
--

CREATE TABLE brackets (
    tour integer NOT NULL,
    seed_id character(3) NOT NULL,
    cbs_url character varying,
    seed smallint
);


ALTER TABLE public.brackets OWNER TO mm;

```

If we know what kind of file it is, we can help you feed it into a database program so you can examine the fields and records.

---

### Post by bjngchn on 2016-04-09
```
 --
-- PostgreSQL database dump
--

SET statement_timeout = 0;
SET lock_timeout = 0;
SET client_encoding = 'UTF8';
SET standard_conforming_strings = on;
SET check_function_bodies = false;
SET client_min_messages = warning;

SET search_path = public, pg_catalog;

SET default_with_oids = false;


```

---

### Post by SeijiSensei on 2016-04-09
OK.  Well first you'll need to install the PostgreSQL server on the machine.  

1) Install postgresql with
```
sudo apt-get install postgresql
```

2) Next create a pg user with the same name as your login account.  To do this, you first need to become the "postgres" user which has administrative privileges on the server:
```
sudo su
[enter your password]
su postgres
createuser -d yourusername
exit
exit

```
The "-d" switch allows that user to create new databases.

3) You should now be back at the prompt running as "yourusername". Create a new database called test
```
createdb test
```

4) Finally, populate the database with the data in your .sql file
```
psql test < /path/to/file.sql
```

If all goes well, you should have a database called test.  To see what's there, use the "psql" client like this:
```
psql test
[server displays banner]
test=> \d

```
The \d command will list all the tables and other objects in the database.  To examine the structure of a specific table, use "\d tablename".  To see the first five records in the table, use the SQL command:
```
test=> select * from tablename limit 5;
```
Note the semicolon at the end.  All SQL commands are terminated with a semicolon.  Also if you use strings, encase them in single quotes like this:
```
test=> select * from users where username='SeijiSensei';
```

Beyond that you'll need to learn some SQL, or use a graphical client like phppgadmin, or LibreOffice Base, or, as I sometimes do, Microsoft Access via the "ODBC" connector for PostgreSQL.  All of this will require some work on your part, of course.  You might start with something like this: [http://www.postgresqltutorial.com/](http://www.postgresqltutorial.com/)

---

### Post by bjngchn on 2016-04-09
I'm stuck at 4th step.  When I type:  psql test < /path/to/file.sql  I get:   No such file or directory.  although there is such a file.

---

### Post by howefield on 2016-04-10
> **bjngchn said:**
> I'm stuck at 4th step.  When I type:  psql test < /path/to/file.sql  I get:   No such file or directory.  although there is such a file.

You did use the real actual path to your file and not /path/to/file.sql, yes ?

---

### Post by bjngchn on 2016-04-10
Yes, but I realized I had to start the path with ~/...  After doing this I get something which  contains some errors and  ends with ALTER TABLE line.

---

### Post by bjngchn on 2016-04-10
I get something until the word  "Beyond" (last paragraph), but no useful data up to that part, and there are error lines as output in one of those commands. ... What did we achieve until that point: Creating "test"? We had a .sql file. Wasn't it a database already?  I just need to be able to search and view lines. I'm not familiar with technical programming language. For example I don't know what kind of things count as "client". Thanks a lot for help up to this point. I may also need directions for getting a useful result in the easiest/fastest way. There must be an easy way to use this data without learning how exactly it works.

---

### Post by SeijiSensei on 2016-04-11
To "use" the data?  No.  The only way you can use the data is to read it into PostgreSQL so you can query it.

What exactly are you trying to find in this data?  A 10 GB file does not lend itself well to browsing.  Are you looking for specific text strings?  Have you tried 
```
grep 'some string' /path/to/file.sql
```
That will list all the lines containing "some string".  Scanning a 10 GB file for a specific string will be a slow process though.

---

### Post by bjngchn on 2016-04-12
grep works well. Thanks. And also it would be great if I can turn search results (coming from grep) into a text file.

---

### Post by SeijiSensei on 2016-04-12
```
grep 'some string' /path/to/file.sql > /path/to/somefile
```
That puts all the results of grep into somefile.  If you run multiple commands and want to append the results to an existing file, use ">>" rather than ">".  The latter creates the file anew each time.

---

### Post by bjngchn on 2016-04-17
Very useful info. Thanks to all, especially to SeijiSensei .

---

