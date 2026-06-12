---
title: "Delete a line in a file by script"
date: 2007-08-16
forum: General Help
---

### Post by hraposo on 2007-08-16
If I in one script to place the line:

echo “deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) to dapper universe” >> /etc/apt/sources.list

this adds a repository sources.list.

**It has some form to erase a line of a file or commenting, by one script?**

---

### Post by heimo on 2007-08-16
> **hraposo said:**
> If I in one script to place the line:

echo “deb [ftp://ftp.videolan.org/pub/videolan/ubuntu](ftp://ftp.videolan.org/pub/videolan/ubuntu) to dapper universe” >> /etc/apt/sources.list

this adds a repository sources.list.

**It has some form to erase a line of a file or commenting, by one script?**

This may be less than optimal... (read: even bad) ... solution, but I'd try something like:

```
cp /etc/apt/sources.list /etc/apt/sources.list_backup
cat /etc/apt/sources.list_backup | grep -v “line you want to remove” > /etc/apt/sources.list


```

This is tiny bit cleaner:
```
cp /etc/apt/sources.list /etc/apt/sources.list_backup
grep -v “line you want to remove” /etc/apt/sources.list_backup > /etc/apt/sources.list
```

---

### Post by pmg on 2007-08-17
Another approach if, say, you want to remove line #4 from a file:
```
awk 'NR!=4' file1 > file2
```
The default action of awk is print out the line, and the above addresses every line but the fourth one, so every other line is written to stdout, which is redirected into file2.

---

### Post by eentonig on 2007-08-17
Doesn't sed help you?

sed 's/<your line or regexpression to remove>/<replacement characters or blank for nothing>/'

---

