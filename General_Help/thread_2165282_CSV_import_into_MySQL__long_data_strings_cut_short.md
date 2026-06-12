---
title: "CSV import into MySQL : long data strings cut short"
date: 2013-08-04
forum: General Help
---

### Post by yanvolking on 2013-08-04
Hello Community,

I am trying to import a CSV file into a MySQL database.  The origin of the CSV file is a database table.  Some of the cells in the original table hold very long strings of data, several hundred words or more in some cases.  The ideal field type for this column would be "TEXT" or "LONGTEXT".  The problem is that as I am not sure how many columns correspond to this CSV file, I use the basic import function which establishes the table structure automatically.  Once done, the column where these long strings go is put as VARCHAR (4899) but the cell only shows the first two or three words and then it cuts off.  I then edit the column and turn it to TEXT with length 65000, but the text remains cut.

I have also tried the following: empty the table of its data (but maintain its structure) convert the column where the long strings go to LONGTEXT and then re-import the CSV file but the process aborts with the following comment : "Invalid column count in CSV input on line 1."

Can anyone advise me on how to deal with the importing of CSV files with sporadic very large strings in certain cells?

---

