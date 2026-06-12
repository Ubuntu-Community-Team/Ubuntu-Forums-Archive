---
title: "Compare 2 directories and extract the Differences to a 3rd Folder"
date: 2008-01-04
forum: General Help
---

### Post by bohn002 on 2008-01-04
Maybe I just need a Kdiff tutoral....
I have an original folder, Folder A. I took the original folder and made changes to its files and its in Folder B. I want to compare A and B and then take the files that appear in B and not A and put them in folder C. And then take the files that show up in A but not B and put them in C.

make sense?

I have been trying with Meld and Kdiff but I just cant get it to work right.

---

### Post by markharding557 on 2008-01-04
hello i'll try to help,disk usage analyser(baobab)can show you file trees,folder/file sizes and numbers of files within.
can't figure out what you are trying to achieve though

---

### Post by geraldm on 2008-01-05
There are tools for your situation.  
A is to be unchanged.
B (or A-0.1+) contains only changed files, and is in the same parent directory as A.
make a tar file of the directory A before any changes are made.
```

mkdir tmp
tar -cvf tmp/A.tar A
# create a difference file for each file that appears in B; collect them in one file, A+.diff
diff -ua A/file1 B/file1 >> tmp/A+.diff
diff -ua A/file2 B/file2 >> tmp/A+.diff
# when all patches are in tmp/A+.diff
cd tmp
tar -xvf ../A.tar
cd A
# apply the changes to this directory
patch -p1 -i ../A+.diff
# Ok to change the name of the directory to C
cd .. && mv A C

```
look up the options for diff and patch in the manpages. 

Gerald

---

