---
title: "How to read big CSV files"
date: 2023-03-04
forum: General Help
---

### Post by gipsyshadow on 2023-03-04
I've to search informations inside a 300MB CSV file downloaded from the web. I've already tried with LibreOffice CALC but rows reach about 1 million so not all the CSV content can be showed/managed, many rows are missed (and in MS Office is even worse!)
My goal is to order data within this CSV so I've not only to open it but I've to manage its inside data to grab only what I'm interested about therefore converting it to a PDF/TXT is not a solution for me.
It could be interesting if I could split it in 2 or more parts and manage each single part one by one but I don't know if it's possible.
Can you help me?

---

### Post by MAFoElffen on 2023-03-04
The most efficient way I can think of, is to treat that as data... That s what you are doing. Using that as data to work against.

SQL databases handle large amounts of data well. Import the csv file into an SQL Database, as data, so that you can run SQL queries against it.

Just a thought.

---

### Post by Holger_Gehrke on 2023-03-04
If you just want to split the file then you might want to take a look at the man page for 'split' ...

If you want something that allows you to do a bit of filtering - so you only get data that is interesting to you - then you could write a small script using 'awk'.

Both of these tools should be installed by default (split is part of the package coreutils and GNU awk is in gawk).

Alternatively it might be an idea to set up a database and import the CSV. Either MariaDB or PostgreSQL should be easily up to it and you could then use LibreOffice Base as a frontend.

Holger

---

### Post by Impavidus on 2023-03-04
Once you've more than a few thousand lines of data, spreadsheet programs become a PITA. Text editors are completely useless for such files. My way of handling such files is to write my own program to deal with it, in whatever programming language I like.

---

### Post by MAFoElffen on 2023-03-04
>  
RE: [Why Excel spreadsheets are bad for business: data errors & solutions]("https://thedatalab.com/news/why-excel-spreadsheets-are-bad-for-business-data-errors-solutions/")

Size Limitations

There is a limit in the number of rows a spreadsheet can store, meaning that organizations must eventually work over multiple files (creating more room for error).Jan 2, 2021

If you have  file of data with over 500 rows, I consider that a database candidate. You mentioned "a million". Almost every database has a facility to import CSV files to their database files. (Even sqlite.)

Unfortunately, LibreOffice Base is not one of those. It wants you to import in Calc, create the database table, then paste the rows into Base. I don't see that happening for that file. LOL

---

### Post by monkeybrain20122 on 2023-03-04
If you have file that big, spreadheet is no longer an appropriate tool, you need real data analysis software to do the job, I have handled some very big datasets with R (using special packages for big data), python is another candidate. Or as MAFoElffen said, treat it as a database and use sql tools to query it.

---

### Post by gipsyshadow on 2023-03-05
Solved. I just searched "split" within ubuntu software and tried "gnome split" and it worked quite fine for my goal and this was the fastest and easiest way for me.
I splitted the CSV file in 2 parts and managed them with LIbreOffice CALC then I could see each file/sheet was made up of about 850k rows therefore the original CSV'd made up of about 1.7 millions rows.
Well, filtering data was not so "fast" and often CALC got frozen *but* it didn't mean CALC stopped to filter/search/work, it's just a message that means: "ok, my job is getting hard but I go on working but now I just don't know if I take 30 seconds or 3 hours to complete it; do you want me to stop?". After a couple of times I understood its "behavior" and I just ignored those messages, I just went away from my PC to do other things, I went back after a couple of minutes, that message was no more on the screen and the search was done. I guess this freeze-like message appears if CALC can't get any result after 400k rows or so.
Hope this helps :) Thanks.

---

### Post by dragonfly41 on 2023-03-05
Although problem solved I throw this command line script if you search for a text *within* the large file

[https://github.com/phiresky/ripgrep-all](https://github.com/phiresky/ripgrep-all)

Very fast.

---

