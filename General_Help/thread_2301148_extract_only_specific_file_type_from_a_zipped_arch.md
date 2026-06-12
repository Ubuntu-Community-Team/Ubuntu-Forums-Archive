---
title: "extract only specific file type from a zipped archive?"
date: 2015-10-31
forum: General Help
---

### Post by onlineaddy on 2015-10-31
I wonder if it's at all possible to extract a specific file, e.g. only pdf files, from a zipped archive that contains also other files and zipped folders in it. Example:

archive.zip:
========
1.zip:
- file.pdf
- file2.pdf
- file37.txt
2.zip:
- file.png
- file3.pdf
- file25.jpg

Say I only wanted to extract file.pdf, file2.pdf and file3.pdf to a folder, how would I go about doing that? 
Imagine the archive is huge and contains hundreds of files in many different .zip archives.
Thanks.

---

### Post by sudodus on 2015-10-31
If you use the GUI program ***file-roller***, you can sort the content of the archive by file type. mark all files of the type you want to extract, and extract them.

If you use the command line program ***unzip***, you can specify which files you want to extract.

1. Test by only listing

full list

```
unzip -l 1234.zip
Archive:  1234.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
       40  2012-03-31 11:38   t1
       98  2012-03-31 11:40   t2
      113  2015-05-10 16:43   teatea
      106  2015-05-10 11:25   teatimer
      221  2011-11-19 12:23   test.sh
      103  2014-06-06 17:55   tin
     2054  2014-06-06 17:55   tlog
    81572  2012-12-23 03:23   ttt.jpg
     6611  2012-07-03 05:06   ttt.tgz
     1951  2014-06-06 17:54   tut
---------                     -------
    92869                     10 files

```

limited list (only files with g in the extension)

```
unzip -l 1234.zip *.*g* -d exdir
caution:  not extracting; -d ignored
Archive:  1234.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
    81572  2012-12-23 03:23   ttt.jpg
     6611  2012-07-03 05:06   ttt.tgz
---------                     -------
    88183                     2 files

```

2. Extracting

```
unzip 1234.zip *.*g* -d exdir
Archive:  1234.zip
  inflating: exdir/ttt.jpg           
 extracting: exdir/ttt.tgz           

```

In other words, you can use an expression with wild-cards to specify what you want to extract. I used ***.*g***, you can use ***.pdf** or **file*.pdf** to extract pdf files.

See ```
man unzip
``` for more details.

---

### Post by onlineaddy on 2015-10-31
Thank you, I will try that. :)

---

