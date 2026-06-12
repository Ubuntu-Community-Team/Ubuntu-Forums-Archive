---
title: "tar czvf default file list sequence"
date: 2007-09-13
forum: General Help
---

### Post by steveneo on 2007-09-13
I use tar to backup my subversion folder. In subversion revs directory, it has many files named by number, which is increased by time. For instance, I check in a file. SVN will create a new file named 59 if it already had 1~58.

I use: tar czvf backup.tar.gz svn-directory. 

In ubuntu server 6.04, the sequence is follow by the incremental sequence of file name. For example, the  verbose list is 
..
svn/revs/57
svn/revs/58
svn/revs/59 
..

After I upgarde to 7.04. The file list in tar zip are mess, absolutely unsorted. Even I unzip this tar to ubuntu 6.0.4 and re-zip svn directory. It still in unsorted sequence.

So what is the tar default sequence to package? could I fix this problem?

---

### Post by HermanAB on 2007-09-13
Hmm?  Just pipe whatever output you want to look at through 'sort':
ls | sort
tar -t whatever.tgz | sort

Cheers,

Herman

---

### Post by steveneo on 2007-09-13
Herman,
It is better than original. but I hope the list should be number sequence. How can I extract last part number and do sort -n?
Currently, the tar verbose is like:
...
/var/svn/main/db/revs/398
/var/svn/main/db/revs/399
/var/svn/main/db/revs/400
..

---

### Post by steveneo on 2008-01-04
I tried tar in 7.10, it is still working in unexpected way, it looks like below when using
tar cvf  dep.tar dependenecies/
....
dependencies/db/revs/94
dependencies/db/revs/98
dependencies/db/revs/53
dependencies/db/revs/117
dependencies/db/revs/62
dependencies/db/revs/122
dependencies/db/revs/1
dependencies/db/revs/86
....

Although I can use sort the order of output, but it is VERY VERY annoy. 

tar is very mature command in linux, why does it still have such problem. I have to keep using 6.04

---

