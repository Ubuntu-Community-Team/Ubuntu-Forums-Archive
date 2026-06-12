---
title: "Rsync Split by Name Order"
date: 2015-01-06
forum: General Help
---

### Post by dannymichel on 2015-01-06
i have a drive that i want to rsync to 2 different drives on one dedicated server. i want to rsync all folder on this drive from the name on top(which starts with '!!!') to the 'M's. I also want to rsync the folders in this drive from the 'N's to the last folder(which ends in an asian character) to the other drive - all in name order. Any ideas?

---

### Post by SeijiSensei on 2015-01-06
You can use "[globs]("http://tldp.org/LDP/abs/html/globbingref.html")" in this case, although that "!!!" name will still be a problem.  To do all the files from "A-M" use something like 
```
rsync -av [a-m]* target
```
If you have mixed-case names, you'll need to experiment a bit.  I can't recall if [a-m]* matches "Alice."

---

### Post by dannymichel on 2015-01-06
rsync -av  /local/path/+([\!a-mA-M])* me@ipaddress:/media/some
rsync -av  /local/path/+([!\!a-mA-M])* me@ipaddress:/media/some
?

---

### Post by kpatz on 2015-01-06
```
rsync -av /local/path/[\ -m]* server:path1
rsync -av /local/path/[n-z]* server:path2
```

In my experimentation, shell globbing is case insensitive (so files starting with A-M or a-m will appear in the first rsync).  Also, files starting with digits or non-alpha characters (including asian characters) will go into the 1st rsync (the sorting isn't in normal ASCII sequence)  The 2nd will only contain files N through Z.  So you may need to experiment based on the number of files that match the two globs.

To get number of files in each glob:
```
ls /local/path/[\ -m]* | wc | awk '{print $1}'
ls /local/path/[n-z]* | wc | awk '{print $1}'
```
To get total size of files in each glob:
```
du -c /local/path/[\ -m]* | grep total
du -c /local/path/[n-z]* | grep total
```
Adjust the start and end letter of the two globs to get the file counts or sizes about the same (based on your criteria for splitting)

---

