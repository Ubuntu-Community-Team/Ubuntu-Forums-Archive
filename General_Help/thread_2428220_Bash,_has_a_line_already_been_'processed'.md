---
title: "Bash, has a line already been 'processed'?"
date: 2019-10-01
forum: General Help
---

### Post by Drenriza on 2019-10-01
Hi all
I am working with a script to extract a small portion of data from a MySQL database with Bash and "doing something" for each line in the resultset.

Questions

1. Is there a smart way for checking if new data has been written to MySQL instead of creating a cronjob and extracting everything with the limits of the SELECT?

2. If i have a file containing a structure such as
[TABLE="width: 500"]
[TR]
[TD]col header1
[/TD]
[TD]col header 2
[/TD]
[TD]col header 3
[/TD]
[TD]col header 4
[/TD]
[TD]col header 5
[/TD]
[/TR]
[TR]
[TD]timestamp
[/TD]
[TD]dara type 1
[/TD]
[TD]unique
[/TD]
[TD]data type 2
[/TD]
[TD]...
[/TD]
[/TR]
[TR]
[TD]timestamp[/TD]
[TD]data type 1
[/TD]
[TD]unique
[/TD]
[TD]data type 2
[/TD]
[TD]...
[/TD]
[/TR]
[/TABLE]

Is there a good way that i can use Bash to determine what rows have already been processed
and what rows i need to process?

Also if i extract a resultset again and it now have 4 rows instead of the above 3.
Than i determine that row 1 is the header (ignore), and 2 & 3 has already been processed, only 4 is new.

Thanks in advance!
Best regards!

---

### Post by sdsurfer on 2019-10-01
It's not clear exactly what you're doing but my first reaction is

- add both created and last_modified timestamps to your tables
- when your update script runs, record the timestamp somewhere
- then

```
select last_run from script_or_cron_record order by last_run desc limit 1;
```

This will give you the $last_run date, then

```
select * from your_data where last_modified > '$last_run_date';
```

.... then run through the resulting record set. Bonus mods, create a success column on your data set and only mark it true if processing was successful, and if it failed record the failed reason for accounting.

```
select * from your_data where last_modified > '$last_run_date' or processed_successfully = false;
```

---

### Post by Drenriza on 2019-10-02
Thanks for your reply @sdsurfer
I have a database connection with view only, so i cannot add or change anything. 
In my select statement i get (lets say) 10 rows at the beginning of the day and for each row i need to do something, than during the day i get more rows, maybe 50 over the next 8 hours.

I would like to be able to periodiocally check if i have received any new rows besides the initial 10, determine what rows i have already 'processed' and process any new rows.

My question was based on if there was any "clever" way of
1. Checking for new rows (could MySQL push new rows automatically to somewhere, example)
2. Determine what rows have already been processed and what needs processing.

Maybe there was a repo package i could install that had "clever" functionality for this.
I have thought a bit over it myself based on your reply, and a solution that i came up with is that i can
create a MySQL database and create a table with a primary key based on a timestamp.

Than each time i try and add row, if the primary key already exist i will be denied, than i avoid duplicates.
Than in my own database i can add an extra field such as bit "checked"
1 = no.
0 = yes.

Than i extract all entries from my own database and for all "checked = 1", process.

That is what i have thought off so far.

---

### Post by sdsurfer on 2019-10-02
Yes I guess that could work. So this external database has no last modified/created fields? If not IMO that's just poor design.

If it does, I don't think you'd need to go to the extent of creating a second DB, you'd just need to store "last run" timestamp and compare against what's in the DB. A simple file would work for that. Either way.

---

