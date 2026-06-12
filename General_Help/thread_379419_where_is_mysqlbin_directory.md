---
title: "where is mysql/bin directory?"
date: 2007-03-08
forum: General Help
---

### Post by Shantesh on 2007-03-08
i have mysql installed via synaptic, and i am following the php/mysql tutorial on webmonkey, i need mysql/bin directory to do the following
> Copy and paste the following text to a file and save it in MySQL's bin directory. (I'll call the file mydb.dump.)

CREATE TABLE employees (  id tinyint(4) DEFAULT '0' NOT NULL AUTO_INCREMENT,  first varchar(20),  last varchar(20),  address varchar(255),  position varchar(50),  PRIMARY KEY (id),  UNIQUE id (id));INSERT INTO employees VALUES (1,'Bob','Smith','128 Here St, Cityname','Marketing Manager');

INSERT INTO employees VALUES (2,'John','Roberts','45 There St , Townville','Telephonist');

INSERT INTO employees VALUES (3,'Brad','Johnson','1/34 Nowhere Blvd, Snowston','Doorman');


If the lines wrap, make sure that each insert statement is on a new line. Now we'll insert it into the mydb database. From the command line, type:

mysql -u root mydb < mydb.dump



where do i find this bin directory, or if that doesnt exist where should put that dump file to make that command work?

Thanks in advance

---

### Post by vayde on 2007-03-08
The directory you are probably looking for is /var/lib/mysql .

However, you don't need to put that file in that location to use the command you are trying to use.

The following:

```

mysql -uroot -p DbName < DbFile.sql

```

will execute the contents of DbFile.sql on the database called DbName.  It doesn't matter where the file is located.

(as long as you are in the same directory as the file in question  when you run the command that is)

---

