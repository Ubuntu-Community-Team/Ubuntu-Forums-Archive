---
title: "how can I print a msql table to paper?"
date: 2015-01-24
forum: General Help
---

### Post by johnnybgoode on 2015-01-24
until now the only way of having a print-out is with a screendump program. Are there other options?

---

### Post by The Cog on 2015-01-24
Is that mysql, or microsoft sql?

Mysql has mysql-workbench which can export a query result to CSV file. From there you can open with LibreOffice or Gnumeric and then print it.

---

### Post by johnnybgoode on 2015-01-24
tanks, I gonna try it. First I have to install that workbench

---

### Post by Holger_Gehrke on 2015-01-24
Or you could use the command line client and do something like this
```

echo 'query'|mysql -u mysqlusername -p databasename|lpr

```

Replace the query, mysqlusername and databasename. Printing goes to the currently selected default printer. Might produce strange / ugly results, you might have to take care not to exceed the line length limits. You could replace 'lpr' at the end of the pipeline with 'a2ps', this might give slightly prettier results. 

If the query contains single quotes, it might be better to write the query in an editor and write it to a file and do
```

mysql -u mysqlusername -p databasename < file_with_query |lpr

```

Finally, if you want to make the output more presentable, you could either sent it to a file like so
```

mysql -u mysqlusername -p databasename <file_with_query >file_with_results

```
or use the 'tee' command in the mysql client.

---

### Post by johnnybgoode on 2015-01-28
tankx for you reaction The Cog.
 I use MySQL.
I dumped the table and opened libreOffice writer.  This application gave my a warning about limited number of columnns.
All the fields coming on one row.
What do I do wrong?
When I tried with writer, the table give's me a list of comma separated records.

---

### Post by SeijiSensei on 2015-01-28
Open LibreOffice Calc, and from there open the file.  Does it import as a spreadsheet?  

Another option is to use LibreOffice Base and connect to the MySQL server over the network.  Then you can query the data and pass the results to Calc or Writer.

---

### Post by steeldriver on 2015-01-28
Maybe explicitly outputing it as CSV would help? - something like

```

SELECT * from example INTO OUTFILE "/tmp/mysql_outfile.csv" FIELDS ENCLOSED BY '"' TERMINATED BY ',' LINES TERMINATED BY '\n';

```

---

