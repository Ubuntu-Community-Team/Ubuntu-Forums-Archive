---
title: "delete file within subfolder"
date: 2007-09-22
forum: General Help
---

### Post by Impulse666 on 2007-09-22
Background: I have a folder called **Music** on an external drive called **EXTERNAL**.
In that folder are many subfolders, one for each artist and album. 
Problem is, I want to delete all *.txt files in the **Music** folder altogether. I did ```
ls -R > list.txt
``` and searched for the file extensions, then deleted them in each directory manually, and after about 5 minutes of that I thought there had to be a better way. There should be a simple command to delete all *.txt or *.m3u files in both a directory and all subdirectories. 

All help greatly appreciated.

~Nick

---

### Post by yabbadabbadont on 2007-09-22
```
find /media/EXTERNAL/Music -type f \(-name "*.txt" -o -name "*.m3u" \) -exec rm {} \;
```
Just to show that it works:
```

/home/daffy/temp $ ls -lR
.:
total 4
drwxr-xr-x 2 daffy daffy 4096 2007-09-22 21:56 jj/
-rw-r--r-- 1 daffy daffy    0 2007-09-22 21:56 mm.m3u
-rw-r--r-- 1 daffy daffy    0 2007-09-22 21:56 nn.doc
-rw-r--r-- 1 daffy daffy    0 2007-09-22 21:56 oo.txt

./jj:
total 0
-rw-r--r-- 1 daffy daffy 0 2007-09-22 21:56 jj.txt
-rw-r--r-- 1 daffy daffy 0 2007-09-22 21:56 kk.m3u
-rw-r--r-- 1 daffy daffy 0 2007-09-22 21:56 ll.doc
/home/daffy/temp $ find . -type f \( -name "*.txt" -o -name "*.m3u" \) -exec rm {} \;
/home/daffy/temp $ ls -lR
.:
total 4
drwxr-xr-x 2 daffy daffy 4096 2007-09-22 21:57 jj/
-rw-r--r-- 1 daffy daffy    0 2007-09-22 21:56 nn.doc

./jj:
total 0
-rw-r--r-- 1 daffy daffy 0 2007-09-22 21:56 ll.doc

```

---

### Post by Impulse666 on 2007-09-22
excellent thank you very much!

---

