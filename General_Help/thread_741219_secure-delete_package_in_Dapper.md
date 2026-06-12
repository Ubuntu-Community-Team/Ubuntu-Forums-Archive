---
title: "secure-delete package in Dapper?"
date: 2008-03-31
forum: General Help
---

### Post by altonbr on 2008-03-31
I use a program called secure-delete and use the /usr/bin/srm binary regularly. In fact, I've even created a script for my clients desktops that will "Secure Delete Trash" using 'srm -r ~/.Trash' (and some more fault-tolerant checking). Unfortunately, one client had to downgrade to Dapper and now he's stuck with no secure-delete package in the repositories.

Is there a way I can install the earlier secure-delete package (from Fiesty) in Dapper?

The problem is, secure-delete relies on libc6 2.5 or greater but Dapper has 2.3.8, so the dependancies aren't satisfied.

Here's the Feisty secure-delete package info: [http://packages.ubuntu.com/feisty/secure-delete](http://packages.ubuntu.com/feisty/secure-delete)

Thank you for your time.

---

### Post by ajgreeny on 2008-03-31
I think you can cd to the folder and then use the command line ```
shred -uvn # path/to/files
```The #is the number of overwrites the command makes, but in fact the man shred suggests that the command is not really useful in a file systems such as ext3.  I quote from the manual:-
> CAUTION:  Note  that  shred relies on a very important assumption: that the file system overwrites data in place.  This is the traditional way to do things,  but many  modern  file system designs do not satisfy this assumption.  The following are examples of file systems on which shred is not effective, or is not  guaranteed to be effective in all file system modes:
       * log-structured or journaled file systems, such as those supplied with
              AIX and Solaris (and JFS, ReiserFS, XFS, Ext3, etc.)

---

### Post by gsmanners on 2008-03-31
That seems similar to wipe, which should be about the same and is available for Dapper.

[http://packages.ubuntu.com/dapper/wipe](http://packages.ubuntu.com/dapper/wipe)

---

