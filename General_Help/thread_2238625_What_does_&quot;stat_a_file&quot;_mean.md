---
title: "What does &quot;stat a file&quot; mean?"
date: 2014-08-09
forum: General Help
---

### Post by vasa1 on 2014-08-09
I was looking at **man find** and saw this:> GNU find frequently stats files during the processing of the  com&#8208;
       mand  line  itself, before any searching has begun. 

Can someone please explain what "stat" is or does? Is it related to "stat - display file or file system status" in **man stat**?

---

### Post by coldraven on 2014-08-09
From here:
[http://manpages.ubuntu.com/manpages/precise/en/man1/find.1.html](http://manpages.ubuntu.com/manpages/precise/en/man1/find.1.html)

> In each case, the  file  specified  on  the
       command  line  will  have been examined and some of its properties will
       have been saved.

So I guess that "stats files" should have been written as "creates statistics of files".

---

### Post by vasa1 on 2014-08-09
So maybe for **find** to do its job, it needs to find out whether a file is a symbolic link or not and that that is what is meant by "stat" at least in this context.

---

### Post by The Cog on 2014-08-09
I thin in this context it means to query the OS about the status of a file - type, date, permissions etc.
Here is the stat reference for the python programming language: [https://docs.python.org/2/library/os.html#os.stat](https://docs.python.org/2/library/os.html#os.stat)

Although this is for python, the info is retrieved by a call to the OS, and the information returned by the OS would be the same regardless of the programming language making the call.

---

