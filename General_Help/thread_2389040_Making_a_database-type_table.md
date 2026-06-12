---
title: "Making a database-type table?"
date: 2018-04-10
forum: General Help
---

### Post by Chew N Tobacca on 2018-04-10
Hello, forums! It's been a long time and good to be back.. 

Let me explain what I'm trying to do, and perhaps I can get some suggestions. I'm trying to put together a fairly simple table or database to log my Hot Wheels collection. What I'd like to have is 4 or 5 columns (for entries like year, make, model, collection, etc.), and an infinite number of rows, and allow for sorting of the rows. I've tried using spreadsheet software (Libre Office), and I can create the table just fine. But when I try to sort the entries, it only sorts the column and mixes the rows all up. So I'd like to be able to sort using any of the 4 or 5 columns and have the entire row be re-sorted. For example, if I wanted to see all the cars from 1969, I could sort them by year; or if I wanted to see how many of a certain series I have, they can be re-sorted by collection series. I hope I am making sense. 

Is there a way to lock the rows with Libre Office so that they don't get mixed up? Thought I'd come ask here, maybe I'm missing something simple. ](*,)

Thanks in advance,
Chew

---

### Post by sp40140 on 2018-04-10
You don't need a database table for what you want to do.
Libre Calc is more than enough.

Now to sorting issue:
instead of selecting entire column (or header), just click on any of the cells in that column and than go to : Data -> sort (pick either acc or dsc).
If you select the column, it will sort only that one column.

---

### Post by SeijiSensei on 2018-04-10
When you use Data > Sort in LibreOffice Calc, does it highlight the entire block of data?

If you have a table with field names in the first row and data below that, put the cursor under the first field name and hit Data > Sort.  It should highlight the entire data area and will usually assume the first row contains field names.  (If that doesn't happen automatically, click the Options tab in the Sort dialog and check the "Range name includes labels" box.)  Make sure there aren't any empty columns among the data fields or the highlighting will be incorrect.

I do this all the time, but occasionally I have to make sure all the data are included in the sort.

If there's something I missed in your original posting, restate your question, and I'll try again.

---

### Post by Chew N Tobacca on 2018-04-10
Thanks for the replies.

> instead of selecting entire column (or header), just click on any of the cells in that column

Yes, that's where I went wrong. I was selecting the whole column, so it was only sorting that column.

> If you have a table with field names in the first row and data below that, put the cursor under the first field name and hit Data > Sort. It should highlight the entire data area and will usually assume the first row contains field names.  (If that doesn't happen automatically, click the Options tab in the Sort dialog and check the "Range name includes labels" box.)

Another part of my confusion, I hadn't seen that option, so it was mixing the row 1 in with the rest of it. I hoped I could make it behave that way. I'll make another attempt when I get a little more time, and reply back with results and any further questions. 

I appreciate you guys/gals. Very helpful as always!

Thanks,
Chew

---

### Post by oldfred on 2018-04-11
Spread Sheet:
When I sort I do have heading and in view freeze first row, and I click on the top, left empty box that then highlights entire spreadsheet. Then in data, sort I can choose columns.


But I started using spreadsheets with Supercalc on CPM system. It only support enough rows and columns for two large green bar dot matrix pages.
So I started using dBase II, III, IV, MS Access & SQL over time, but still used spreadsheets for smaller amounts of data or estimate type sheets where not data rows & columns.

I now use python for code and SQLite for data, but that has a good sized learning curve.

There are these data bases for collections like yours.
If you put collection in synaptic search you can find multiple apps, including these:
       Collections - music, books, etc: both in repositories
Tellico - qt4 & python, xml for data
[http://tellico-project.org/](http://tellico-project.org/)
Gcstar - perl & gtk, xml for data
[URL="http://www.gcstar.org/"]http://www.gcstar.org/

[/URL]

---

### Post by Chew N Tobacca on 2018-04-12
Reporting back. What you guys suggested worked perfectly. I now have a spreadsheet layout established that functions how I wanted, it's exactly what I hoped for. Thank you! 

And thank you, oldfred, for the collections suggestion. Might be something to check out in the future.

Thanks again for the excellent information.
Chew

---

### Post by SeijiSensei on 2018-04-12
You're welcome.

Might I suggest you use the Thread Tools link at the top to mark this SOLVED.

---

