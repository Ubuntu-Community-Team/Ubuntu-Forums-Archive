---
title: "Help getting Unison to sync"
date: 2018-01-01
forum: General Help
---

### Post by Notre on 2018-01-01
Hi,

I'm trying to get Unison to sync two folders, one on my Ubuntu computer and one on my Mac.  (I was able to get Rsync working earlier, but I want bidirectional syncing, so I'm looking at Unison).  As a test, I created a simple folder on my Ubuntu machine named syncTest that contains two text files, file1.txt and file2.txt.  Then I used this command:

```
unison ~/syncTest/ ssh://admin@Macbook.local//Users/Admin/syncTest
```

The output of the command is this:

```
Contacting server...Connected [//MacBook.local//Users/Admin/syncTest -> //notre-ubuntu//home/notre/syncTest]
Looking for changes
Warning: No archive files were found for these roots, whose canonical names are:
    /home/notre/syncTest
    //MacBook.local//Users/Admin/syncTest
This can happen either
because this is the first time you have synchronized these roots, 
or because you have upgraded Unison to a new version with a different
archive format.  


Update detection may take a while on this run if the replicas are 
large.


Unison will assume that the 'last synchronized state' of both replicas
was completely empty.  This means that any files that are different
will be reported as conflicts, and any files that exist only on one
replica will be judged as new and propagated to the other replica.
If the two replicas are identical, then no changes will be reported.


If you see this message repeatedly, it may be because one of your machines
is getting its address from DHCP, which is causing its host name to change
between synchronizations.  See the documentation for the UNISONLOCALHOSTNAME
environment variable for advice on how to correct this.


Donations to the Unison project are gratefully accepted: 
http://www.cis.upenn.edu/~bcpierce/unison


Press return to continue.[<spc>]   Waiting for changes from server
Reconciling changes


local          MacBook.l...       
dir      ---->            /  [f] 



```

At this point, nothing further happens.  It appears to be sitting indefinitely on my Ubuntu computer.  Any ideas on what might be going wrong?

Thank you!

---

