---
title: "How to search for all files that contain a string"
date: 2013-01-28
forum: General Help
---

### Post by tc101 on 2013-01-28
in 12.04, is there a way to search for all files in a directory that contain the string "Jerry Smith"?

Better yet, all files in a date range that contain the string "Jerry Smith"?

If that can't be done with the standard search tools that come with the package, what is the best add on in the software center that will do it?

I don't want to type in a command in the terminal.

---

### Post by slickymaster on 2013-01-28
```
find /path/to/dir -name "*<string>*"
```

Take a look at find command in Community Ubuntu Documentation, [here]("https://help.ubuntu.com/community/find").

---

### Post by kc1di on 2013-01-28
you can also use grep command

[here a page]("http://www.cyberciti.biz/faq/howto-use-grep-command-in-linux-unix/") that will help.

---

### Post by slickymaster on 2013-01-28
Just know I noticed that you weren't interested in a command in terminal. Sorry about that.

If you're looking for a GUI to do the job, I would recommend you Catfish. It's in the repos, or through the terminal:

```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install catfish
```

---

### Post by kc1di on 2013-01-28
Whoops !!! 

I also missed the statement about no terminal. It really is the easy way to search though , sorry :(

---

### Post by tc101 on 2013-01-28
Thanks.  I tried catfish.  Reading online I see that you need to add other serach engines to it.  I was going to add Beagle but when I searched in ubuntu software center it didn't have beagle.

I tried search monkey and it does what I want.  Is there anything about using catfish that is better than search monkey?

---

### Post by rnerwein on 2013-01-28
> **tc101 said:**
> Thanks.  I tried catfish.  Reading online I see that you need to add other serach engines to it.  I was going to add Beagle but when I searched in ubuntu software center it didn't have beagle.

I tried search monkey and it does what I want.  Is there anything about using catfish that is better than search monkey?
hi
unix/linux is a tool machine - you ain't need additional software.
try: 
grep -inH 'Jerry Smith' `find . -type f` 
this will search all files in the "." tree and if there is a file with the contents you want the 
output is:
./tst:3:irgendwo steht Jerry Smith ?
the filename --> ./tst and the linenumber where your grep matched
i put this line in a test file
cheers

---

### Post by LewisTM on 2013-01-28
Package **recoll** will index any directory, reading pretty much all document types (MS, ODF, PDF). Once this is done, you can go to Advanced Search and find all files containing a certain string, as well as filter by file type and date. Oh, and it's all graphical, no terminal here.

Enjoy!

---

