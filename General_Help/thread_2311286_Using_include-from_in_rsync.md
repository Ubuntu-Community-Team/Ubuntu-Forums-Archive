---
title: "Using include-from in rsync"
date: 2016-01-26
forum: General Help
---

### Post by Contoured_Solution on 2016-01-26
Trying to use rsync to copy only certain file extensions from one directory to another using the "include-from" parameter. My command looks like this:

```
rsync -ravv /exports/clientfiles/ /exports/cloudbackup/ --include-from=include-list.txt
```

And the list file looks like this:

```
+ CLIENT FILES/
+ CLIENT FILES/**.pdf
+ CLIENT FILES/**.PDF
+ RETAINERS/
- *
```

I see the the pattern is successful in matching anything in the first directory as I see lots of " hiding directory CLIENT FILES/SOMEFOLDER" messages, but I can't figure out why it does not match any file ending in PDF in any subdirectory. I was made to understand that ** matches all text and slashes. What am I missing?

---

### Post by ajgreeny on 2016-01-26
I think you need the full pathway to that include-list file but I also see that those folder names contain spaces (never a good idea in Linux if you can avoid it) and probably need escaping either by using quotation marks around the full pathways or using a backslash to escape the space individually, ie 
```
+ CLIENT\ FILES/
+ CLIENT\ FILES/**.pdf
+ CLIENT\ FILES/**.PDF
+ RETAINERS/
- *
```
or
```
+ "CLIENT FILES/"
+ "CLIENT FILES/**.pdf"
+ "CLIENT FILES/**.PDF"
+ RETAINERS/
- *
```
You may also need the full,pathway of the folders.
I am not totally sure if you need the + sign at the start of each line and a quick look at man rsync has not helped me find out that, but it is a long man so I may have missed it.

I do, however use an **--exclude-from=/home/ajgreeny/exclude.txt** and that does not need the + sign; it is just a list of folders in my home to exclude.

---

### Post by Contoured_Solution on 2016-01-28
Removed + symbols and still no dice. How would you format yours if you wanted to only capture, say, PDF files?

---

### Post by SeijiSensei on 2016-01-28
You just want one star, too.  I've also removed the quotation marks and "escaped" the embedded spaces with a backslash.

```

CLIENT\ FILES/
CLIENT\ FILES/*.pdf
CLIENT\ FILES/*.PDF
RETAINERS/

```

This should work if you start rsync in the parent of these directories.  If you want it to work from anywhere, you need full paths in the file like
```
/home/me/CLIENT\ FILES/
```

I try to avoid having embedded spaces in file and directory names just to avoid the machinations required to make them work correctly all the time.

---

