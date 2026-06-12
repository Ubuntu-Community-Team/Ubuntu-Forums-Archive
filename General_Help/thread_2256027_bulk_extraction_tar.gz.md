---
title: "bulk extraction tar.gz"
date: 2014-12-09
forum: General Help
---

### Post by Mohsin_khalid on 2014-12-09
hello guys.

please help me with the script i have thousand of tar.gz files they all are in folders & name and date wise.
i want all of them to be extract in the same folders with the help of script.

please provide any example so that i can easily do it.

---

### Post by TheFu on 2014-12-09
```
cd path-to-output-directory
tar zxvf /path/to/input/files/directory/*tar.gz 

```
Is there a reason that doesn't work?  If there are too many files for the filename expansion to work, use xargs or a while loop with globbing.
[http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/) will help, I'm certain.

Might need to force the output directory with the tar command if the files were stored with absolute paths (i.e. beginning with /).  The tar manpage will have that option - sorry I don't remember it.

---

### Post by nerdtron on 2014-12-09
Be careful on extracting everything as you may fill up your disk space. Also the compressed files are still retained after the extraction.
We can create a script for extracting all for them.

Sample files:
```
kenneth@nerdtron:~/testing$ ll
total 0
-rw-rw-r-- 1 kenneth kenneth 0 Dec  9 11:28 file1.tar.gz
-rw-rw-r-- 1 kenneth kenneth 0 Dec  9 11:28 file2.tar.gz
-rw-rw-r-- 1 kenneth kenneth 0 Dec  9 11:28 file3.tar.gz
-rw-rw-r-- 1 kenneth kenneth 0 Dec  9 11:28 file4.tar.gz
-rw-rw-r-- 1 kenneth kenneth 0 Dec  9 11:28 file5.tar.gz
```

Now for the script to extract them:
```
#!/bin/bash
for i in *.tar.gz; do
tar -zxvf $i;
done
```

---

