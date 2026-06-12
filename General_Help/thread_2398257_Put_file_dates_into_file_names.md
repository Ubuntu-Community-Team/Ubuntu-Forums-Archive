---
title: "Put file dates into file names"
date: 2018-08-09
forum: General Help
---

### Post by raleigh3 on 2018-08-09
I need help putting file dates into the names of some files that I backup.

Ex.

8_9_2018_Ubuntu_Scripts.zip

I currently use zip to create Ubuntu_Scripts.zip.

---

### Post by TheFu on 2018-08-09
Or perhaps you can use a backup tool that handles this for you automatically?  rdiff-backup will, but any competent backup tool will.

If you insist on doing what you have planned, might I strongly suggest you use YYYY-MM-DD format, so things sort better?
The **date** command will let you format output almost anyway you want.  **date "+%F"** is an example. The date manpage has the formatting options, so you can get the format you want, if it is different.

---

### Post by #&amp;thj^% on 2018-08-09
Will this work for you:
```
cp somefile somefile_`date +%d%b%Y`
```

---

### Post by raleigh3 on 2018-08-09
cp Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/_`date +%d%b%Y`

```
cp: cannot stat 'date Ubuntu_Documents.zip': No such file or directory
```

Found my mistake.

cp Ubuntu_Documents.zip /media/andy/MAXTOR_SDB1/Ubuntu_Mate_18.04/Ubuntu_Documents.zip_`date +%d%b%Y_%H_%M`

---

### Post by Holger_Gehrke on 2018-08-09
Those weren't apostrophes, those were backticks. They are an old shorthand for command substitution $( ... ). Using the more readable form the command would read as:```
cp somefile somefile_$(date +%d%b%Y)
```

Holger

---

### Post by #&amp;thj^% on 2018-08-09
That would be expected.
Example:
```
cp /home/me/Music/'Rock Solid Radio'/ /home/me/Music/'Rock Solid Radio'/_`date +%d%b%Y`

```
Make sure the path is correct.

---

