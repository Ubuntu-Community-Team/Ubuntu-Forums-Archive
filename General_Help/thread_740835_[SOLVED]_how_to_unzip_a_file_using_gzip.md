---
title: "[SOLVED] how to unzip a file using gzip?"
date: 2008-03-31
forum: General Help
---

### Post by Rytron on 2008-03-31
Hi,
I know that while in the terminal you can type gzip newfile

to zip the file titled newfile.

How can I unzip this file using gzip? I find the man gzip instructions hard to follow.

Thanks.

---

### Post by rufius on 2008-03-31
The simple way is using the command "gunzip <file>".

I'm not sure there is a direct way with gzip? Those two commands are bundled together though so any system that has gzip, should have its complement, gunzip.

-Zac

---

### Post by cdenley on 2008-03-31
```

man gzip

```
Gives a brief summary of all the different commands you could use.

---

### Post by chilinski on 2008-03-31
An *.gz file can be unzipped with tar:

tar zxvf file.tar.gz

---

### Post by Slushdoot on 2008-03-31
> **chilinski said:**
> An *.gz file can be unzipped with tar:

tar zxvf file.tar.gzThat's only if it's a tar.gz or .tgz archive.  A plain old .gz won't work if you try to untar it since it wasn't tar'd in the first place.

gzip file.txt
becomes file.txt.gz

extract it with 
gunzip gile.txt.gz
it becomes file.txt

Try it out! :)

---

