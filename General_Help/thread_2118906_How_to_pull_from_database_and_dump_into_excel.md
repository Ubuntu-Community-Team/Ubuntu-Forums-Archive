---
title: "How to pull from database and dump into excel"
date: 2013-02-22
forum: General Help
---

### Post by taylorpIII on 2013-02-22
We are working with a perl script that pulls serial numbers for cell phones from various websites.  I need to pull the serial numbers the from our database ("DBI:mysql:test"), and dump them into an excel spreadsheet.  

Any thoughts?  My terminal commands are a bit rusty.

---

### Post by slickymaster on 2013-02-22
```
mysql -u username -p password database -B -e "SELECT * FROM table;" | sed 's/\t/","/g;s/^/"/;s/$/"/;s/\n//g' > filename.csv
```

username is your mysql username
password is your mysql password
database is your mysql database
table is the table you want to export

The -B option will delimit the data using tabs and each row will appear on a new line.
The -e option denotes the MySQL command to run, in your case the "SELECT" statement.
The "sed" command contains three sed scripts:
s/\t/","/g;s/^/"/ - this will search and replace all occurences of 'tabs' and replace them with a ",".
s/$/"/; - this will place a " at the start of the line.
s/\n//g  - this will place a " at the end of the line.

---

### Post by taylorpIII on 2013-02-22
Thanks for the code.  I'm sure its going to work but we're doing something wrong.  The name of the database is "test", and the names of the tables were trying to pull are: {ESN} {MSL} and {MODEL}.  It looks like this in the script:

"<td>$product->{ESN}</td>";
"<td>$product->{MSL}</td>";
"<td>$product->{MODEL}</td>";

I tried the ESN by itself.  When I hit enter the error message says:  ERROR 1146 (42S02)at line 1:  Table 'test.ESN' doesn't exist

What are we doing wrong?

Thx.

---

### Post by schragge on 2013-02-22
So, you want to combine data from the three tables? Or ESN, MSL, and MODEL are three fields from **one** table?

---

### Post by schragge on 2013-02-22
@**slickymaster**
*SELECT &#8230; INTO OUTFILE* in MySQL allows specifying the output format:
```

SELECT * INTO OUTFILE 'filename.csv'
  FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
  LINES TERMINATED BY '\n'
FROM test;

```

---

### Post by slickymaster on 2013-02-22
> **taylorpIII said:**
> Thanks for the code.  I'm sure its going to work but we're doing something wrong.

Just to let you that I noticed an error on the code I previously post and already edit it to correct it. I have skipped a space in the switch and option for the password of the user.

---

### Post by slickymaster on 2013-02-22
> **schragge said:**
> @**slickymaster**
*SELECT … INTO OUTFILE* in MySQL allows specifying the output format:
```

SELECT * INTO OUTFILE 'filename.csv'
  FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
  LINES TERMINATED BY '\n'
FROM test;

```

You're assuming that the OP has direct access to the server's file system, right?

---

### Post by taylorpIII on 2013-02-22
They are three separate tables.  We want to pull from all three.  We're going to try your revisions now.

---

### Post by slickymaster on 2013-02-22
> **schragge said:**
> @**slickymaster**
*SELECT &#8230; INTO OUTFILE* in MySQL allows specifying the output format:
```

SELECT * INTO OUTFILE 'filename.csv'
  FIELDS TERMINATED BY ',' OPTIONALLY ENCLOSED BY '"'
  LINES TERMINATED BY '\n'
FROM test;

```

I guess that using the -B option to the mysql command would also work, doing it one table at a time.
This option will generate TSV (tab separated) files which can quite easily be imported into Excel:
```
echo 'SELECT * FROM table' | mysql -B -uxxx -pyyy database
```

-uxxx stands for the user
-pyyy stands for the user password

---

### Post by taylorpIII on 2013-02-22
ERROR 1146 (42S02) at line 1:  Table 'test.ESN' doesn't exist. And yes the OP has direct access to the server.

---

